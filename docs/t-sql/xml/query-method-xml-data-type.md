---
title: query() 方法（xml 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb7f52a1861567630229b31679b3d84cb42eaeae
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703925"
---
# <a name="query-method-xml-data-type"></a>query() 方法（xml 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  对 xml 数据类型的实例指定 XQuery。 结果为 xml 类型。 该方法返回非类型化的 XML 实例。  
  
## <a name="syntax"></a>语法  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>参数  
 XQuery  
 字符串，查询 XML 实例中的 XML 节点（如元素、属性）的 XQuery 表达式。  
  
## <a name="examples"></a>示例  
 本节提供使用 xml 数据类型的 query() 方法的示例。  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. 对 xml 类型的变量使用 query() 方法  
 以下示例声明 xml 类型的变量 @myDoc 并将 XML 实例分配给它。 然后使用 query() 方法对文档指定 XQuery。  
  
 该查询检索 <`ProductDescription`> 元素的 <`Features`> 子元素：  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 结果如下：  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. 对 XML 类型列使用 query() 方法  
 在以下示例中，使用 query() 方法对 AdventureWorks 数据库中 xml 类型的 CatalogDescription 列指定 XQuery：  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 请注意上述查询的以下方面：  
  
-   CatalogDescription 列是类型化的 xml 列。 这表示它包含一个与之相关联的架构集合。 在 [XQuery Prolog](../../xquery/modules-and-prologs-xquery-prolog.md) 中，namespace 关键字用于定义以后在查询主体中使用的前缀。  
  
-   query() 方法构造 XML，即包含 ProductModelID 属性的 <`Product`> 元素，其中 ProductModelID 属性值是从数据库中检索的。 有关 XML 构造的详细信息，请参阅 [XML 构造 (XQuery)](../../xquery/xml-construction-xquery.md)。  
  
-   WHERE 子句中的 [exist() 方法（XML 数据类型）](../../t-sql/xml/exist-method-xml-data-type.md)用于仅查找包含 XML 中的 <`Warranty`> 元素的行。 namespace 关键字将再次用于定义两个命名空间前缀。  
  
 下面是部分结果：  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 请注意，query() 方法和 exist() 方法都声明 PD 前缀。 在这些情况下，可以使用 WITH XMLNAMESPACES 首先定义前缀，然后在查询中使用它。  
  
```  
WITH XMLNAMESPACES 
(  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>另请参阅  
 [使用 WITH XMLNAMESPACES 将命名空间添加到查询](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [类型化的 XML 与非类型化的 XML 的比较](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [创建 XML 数据的实例](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml 数据类型方法](../../t-sql/xml/xml-data-type-methods.md)   
 [XML 数据修改语言 (XML DML)](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
