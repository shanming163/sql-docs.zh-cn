---
title: 在.NET 环境中使用 SQLXML 大容量加载 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b832f6d92b847ee823a350559dbc54fd35a13ec2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175877"
---
# <a name="using-sqlxml-bulk-load-in-the-net-environment"></a>在 .NET 环境中使用 SQLXML 大容量加载
  本主题说明如何在 .NET 环境中使用 XML 大容量加载功能。 有关 XML 大容量加载的详细信息，请参阅[执行大容量加载的 XML 数据&#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)。  
  
 若要从托管环境使用 SQLXML 大容量加载 COM 对象，需要添加对此对象的项目引用。 这将围绕该大容量加载 COM 对象生成一个托管的包装接口。  
  
> [!NOTE]  
>  托管的 XML 大容量加载不使用托管流并且要求围绕本机流的包装。 SQLXML 大容量加载组件将不在多线程环境中运行（“[MTAThread]”属性）。 如果尝试在多线程环境中运行大容量加载组件，获取具有以下附加信息的 InvalidCastException 异常:"接口 SQLXMLBULKLOADLib.ISQLXMLBulkLoad 的 QueryInterface 失败。" 解决方法是使包含大容量加载对象单线程可访问的对象 (例如，通过使用 **[STAThread]** 特性，如示例所示)。  
  
 本主题提供一个 C# 应用程序的工作示例，用于将 XML 数据大容量加载到数据库中。 请按照以下步骤创建工作示例：  
  
1.  创建以下表：  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  将以下架构保存在文件 (schema.xml) 中：  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  将以下示例 XML 文档保存在文件 (data.xml) 中：  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  启动 Visual Studio。  
  
5.  创建 C# 控制台应用程序。  
  
6.  从**项目**菜单中，选择**添加引用**。  
  
7.  在中**COM**选项卡上，选择**Microsoft SQLXML Bulkload 4.0 类型库**(xblkld4.dll) 并单击**确定**。 你将看到**Interop.SQLXMLBULKLOADLib**在项目中创建的程序集。  
  
8.  用下面的代码替换 Main() 方法。 更新**ConnectionString**属性和架构和数据文件的文件路径。  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. 若要在您创建的表中加载 XML，请生成并运行该项目。  
  
    > [!NOTE]  
    >  还可以使用 tlbimp.exe 工具添加对大容量加载组件 (xblkld4.dll) 的引用，该工具作为 .NET framework 的一部分提供。 该工具为本机 DLL (xblkld4.dll) 创建一个托管包装，然后该包装可用于任何 .NET 项目中。 例如：  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     这将创建可用于 .NET Framework 项目中的托管包装 DLL (SQLXMLBULKLOADLib.dll)。 在 .NET Framework 中，您添加对新创建的 DLL 的项目引用。  
  
## <a name="see-also"></a>请参阅  
 [执行大容量加载 XML 数据的&#40;SQLXML 4.0&#41;](bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
