---
title: 維護名稱/值組 (C#)
ms.date: 07/20/2015
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 28c01ce17881ffe7e8fcc35e2c23dec85d50955d
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578873"
---
# <a name="maintaining-namevalue-pairs-c"></a><span data-ttu-id="0f9b7-102">維護名稱/值組 (C#)</span><span class="sxs-lookup"><span data-stu-id="0f9b7-102">Maintaining Name/Value Pairs (C#)</span></span>
<span data-ttu-id="0f9b7-103">許多應用程式都必須維護妥善保存為成對名稱/值的資訊。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-103">Many applications have to maintain information that is best kept as name/value pairs.</span></span> <span data-ttu-id="0f9b7-104">這類資訊可能是組態或全域設定的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-104">This information might be configuration information or global settings.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0f9b7-105"> 包含一些有助您輕鬆保存成對名稱/值組的方法。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-105"> contains some methods that make it easy to keep a set of name/value pairs.</span></span> <span data-ttu-id="0f9b7-106">您可以將該資訊保存為屬性或一組子項目。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-106">You can either keep the information as attributes or as a set of child elements.</span></span>  
  
 <span data-ttu-id="0f9b7-107">將資訊保存為屬性或子項目的其中一個差異在於，屬性所擁有的條件約束中，僅能有一個具有項目之特定名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-107">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="0f9b7-108">這項限制不適用於子項目。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-108">This limitation does not apply to child elements.</span></span>  
  
## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="0f9b7-109">SetAttributeValue 和 SetElementValue</span><span class="sxs-lookup"><span data-stu-id="0f9b7-109">SetAttributeValue and SetElementValue</span></span>  
 <span data-ttu-id="0f9b7-110">可簡化保存成對名稱/值的兩個方法為 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 和 <xref:System.Xml.Linq.XElement.SetElementValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-110">The two methods that facilitate keeping name/value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="0f9b7-111">這些兩個方法具有類似的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-111">These two methods have similar semantics.</span></span>  
  
 <span data-ttu-id="0f9b7-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 可以加入、修改或移除項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-112"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, or remove attributes of an element.</span></span>  
  
-   <span data-ttu-id="0f9b7-113">如果您呼叫的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 具有不存在之屬性的名稱，此方法會建立一個新的屬性，並將其加入到指定的項目中。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-113">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that does not exist, the method creates a new attribute and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="0f9b7-114">如果您呼叫的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 具有現有屬性的名稱以及某些指定的內容，屬性的內容會取代為指定的內容。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="0f9b7-115">如果您呼叫具有現有屬性之名稱的 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>，並為內容指定 Null，該屬性會從其父代移除。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify null for the content, the attribute is removed from its parent.</span></span>  
  
 <span data-ttu-id="0f9b7-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> 可以加入、修改或移除項目的子項目。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-116"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, or remove child elements of an element.</span></span>  
  
-   <span data-ttu-id="0f9b7-117">如果您呼叫的 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 具有不存在之子項目的名稱，此方法會建立一個新的項目，並將其加入到指定的項目中。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-117">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that does not exist, the method creates a new element and adds it to the specified element.</span></span>  
  
-   <span data-ttu-id="0f9b7-118">如果您呼叫的 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 具有現有項目的名稱以及某些指定的內容，項目的內容會取代為指定的內容。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>  
  
-   <span data-ttu-id="0f9b7-119">如果您呼叫具有現有項目之名稱的 <xref:System.Xml.Linq.XElement.SetElementValue%2A>，並為內容指定 Null，該項目會從其父代移除。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify null for the content, the element is removed from its parent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f9b7-120">範例</span><span class="sxs-lookup"><span data-stu-id="0f9b7-120">Example</span></span>  
 <span data-ttu-id="0f9b7-121">下列範例會建立沒有屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-121">The following example creates an element with no attributes.</span></span> <span data-ttu-id="0f9b7-122">接著，它會使用 <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> 方法來建立並維護成對名稱/值的清單。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-122">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as attributes.  
root.SetAttributeValue("Top", 22);  
root.SetAttributeValue("Left", 20);  
root.SetAttributeValue("Bottom", 122);  
root.SetAttributeValue("Right", 300);  
root.SetAttributeValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
  
// Replace the value of Top.  
root.SetAttributeValue("Top", 10);  
Console.WriteLine(root);  
  
// Remove DefaultColor.  
root.SetAttributeValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="0f9b7-123">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0f9b7-123">This example produces the following output:</span></span>  
  
```xml  
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />  
<Root Top="10" Left="20" Bottom="122" Right="300" />  
```  
  
## <a name="example"></a><span data-ttu-id="0f9b7-124">範例</span><span class="sxs-lookup"><span data-stu-id="0f9b7-124">Example</span></span>  
 <span data-ttu-id="0f9b7-125">下列範例會建立沒有子項目的項目。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-125">The following example creates an element with no child elements.</span></span> <span data-ttu-id="0f9b7-126">接著，它會使用 <xref:System.Xml.Linq.XElement.SetElementValue%2A> 方法來建立並維護成對名稱/值的清單。</span><span class="sxs-lookup"><span data-stu-id="0f9b7-126">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name/value pairs.</span></span>  
  
```csharp  
// Create an element with no content.  
XElement root = new XElement("Root");  
  
// Add a number of name/value pairs as elements.  
root.SetElementValue("Top", 22);  
root.SetElementValue("Left", 20);  
root.SetElementValue("Bottom", 122);  
root.SetElementValue("Right", 300);  
root.SetElementValue("DefaultColor", "Color.Red");  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Replace the value of Top.  
root.SetElementValue("Top", 10);  
Console.WriteLine(root);  
Console.WriteLine("----");  
  
// Remove DefaultColor.  
root.SetElementValue("DefaultColor", null);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="0f9b7-127">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="0f9b7-127">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Top>22</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
  <DefaultColor>Color.Red</DefaultColor>  
</Root>  
----  
<Root>  
  <Top>10</Top>  
  <Left>20</Left>  
  <Bottom>122</Bottom>  
  <Right>300</Right>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f9b7-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f9b7-128">See Also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>  
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>  
- [<span data-ttu-id="0f9b7-129">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f9b7-129">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
