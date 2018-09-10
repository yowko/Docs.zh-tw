---
title: 移除 DOM 中項目節點的屬性
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65fd6d2baae29c72241350e4568faf09b9c71f39
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44188135"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a><span data-ttu-id="adf67-102">移除 DOM 中項目節點的屬性</span><span class="sxs-lookup"><span data-stu-id="adf67-102">Removing Attributes from an Element Node in the DOM</span></span>
<span data-ttu-id="adf67-103">有許多方法可用來移除屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-103">There are many ways to remove attributes.</span></span> <span data-ttu-id="adf67-104">其中一種技術是從屬性集合中移除它們。</span><span class="sxs-lookup"><span data-stu-id="adf67-104">One technique is to remove them from the attribute collection.</span></span> <span data-ttu-id="adf67-105">若要如此做，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="adf67-105">To do this, the following steps are performed:</span></span>  
  
1.  <span data-ttu-id="adf67-106">使用 `XmlAttributeCollection attrs = elem.Attributes;`，從項目取得屬性集合。</span><span class="sxs-lookup"><span data-stu-id="adf67-106">Get the attribute collection from the element using `XmlAttributeCollection attrs = elem.Attributes;`.</span></span>  
  
2.  <span data-ttu-id="adf67-107">使用下列三種方法之一，從屬性集合移除屬性：</span><span class="sxs-lookup"><span data-stu-id="adf67-107">Remove the attribute from the attribute collection using one of three methods:</span></span>  
  
    -   <span data-ttu-id="adf67-108">使用 <xref:System.Xml.XmlAttributeCollection.Remove%2A> 移除特定屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-108">Use <xref:System.Xml.XmlAttributeCollection.Remove%2A> to remove a specific attribute.</span></span>  
  
    -   <span data-ttu-id="adf67-109">使用 <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> 從集合中移除所有的屬性，並保留不具屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="adf67-109">Use <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> to remove all attributes from the collection and leave the element with no attributes.</span></span>  
  
    -   <span data-ttu-id="adf67-110">使用 <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A>，並透過屬性的索引編號，從屬性集合中移除屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-110">Use <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> to remove an attribute from the attribute collection by using its index number.</span></span>  
  
 <span data-ttu-id="adf67-111">下列方法可從項目節點移除屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-111">The following methods remove attributes from the element node.</span></span>  
  
-   <span data-ttu-id="adf67-112">使用 <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> 移除屬性集合。</span><span class="sxs-lookup"><span data-stu-id="adf67-112">Use <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> to remove the attribute collection.</span></span>  
  
-   <span data-ttu-id="adf67-113">使用 <xref:System.Xml.XmlElement.RemoveAttribute%2A>，依名稱從集合移除單一屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-113">Use <xref:System.Xml.XmlElement.RemoveAttribute%2A> to remove a single attribute by name from the collection.</span></span>  
  
-   <span data-ttu-id="adf67-114">使用 <xref:System.Xml.XmlElement.RemoveAttributeAt%2A>，依索引編號從集合移除單一屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-114">Use <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> to remove a single attribute by index number from the collection.</span></span>  
  
 <span data-ttu-id="adf67-115">還有另一種替代方案是取得項目，再從屬性集合取得屬性，然後直接移除該屬性節點。</span><span class="sxs-lookup"><span data-stu-id="adf67-115">One more alternative is to get the element, get the attribute from the attribute collection, and remove the attribute node directly.</span></span> <span data-ttu-id="adf67-116">若要從屬性集合取得屬性，可以使用名稱 `XmlAttribute attr = attrs["attr_name"];` 及索引 `XmlAttribute attr = attrs[0];`，或是使用命名空間 `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]` 來完整限定名稱。</span><span class="sxs-lookup"><span data-stu-id="adf67-116">To get the attribute from the attribute collection, you can use a name, `XmlAttribute attr = attrs["attr_name"];`, an index `XmlAttribute attr = attrs[0];`, or by fully qualifying the name with the namespace `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.</span></span>  
  
 <span data-ttu-id="adf67-117">無論使用何種方法移除屬性，對移除定義為文件類型定義 (DTD) 中預設屬性的屬性都有特殊限制。</span><span class="sxs-lookup"><span data-stu-id="adf67-117">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the document type definition (DTD).</span></span> <span data-ttu-id="adf67-118">除非移除預設屬性的所屬項目，否則無法移除預設屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-118">Default attributes cannot be removed unless the element they belong to is removed.</span></span> <span data-ttu-id="adf67-119">針對已宣告預設屬性的項目，其預設屬性會永遠存在。</span><span class="sxs-lookup"><span data-stu-id="adf67-119">Default attributes are always present for elements that have default attributes declared.</span></span> <span data-ttu-id="adf67-120">從 <xref:System.Xml.XmlAttributeCollection> 或 <xref:System.Xml.XmlElement> 中移除預設屬性時，會將取代屬性插入至項目的 <xref:System.Xml.XmlAttributeCollection>，並初始化為已宣告的預設值。</span><span class="sxs-lookup"><span data-stu-id="adf67-120">Removing a default attribute from an <xref:System.Xml.XmlAttributeCollection> or from the <xref:System.Xml.XmlElement> results in a replacement attribute inserted into the <xref:System.Xml.XmlAttributeCollection> of the element, initialized to the default value that was declared.</span></span> <span data-ttu-id="adf67-121">如果您的項目定義為 `<book att1="1" att2="2" att3="3"></book>`，則 `book` 項目會具有三個已宣告的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="adf67-121">If you have an element defined as `<book att1="1" att2="2" att3="3"></book>`, then you have a `book` element with three default attributes declared.</span></span> <span data-ttu-id="adf67-122">XML 文件物件模型 (DOM) 實作可保證只要此 `book` 項目存在，它就會具有三個預設屬性：`att1`、`att2` 及 `att3`。</span><span class="sxs-lookup"><span data-stu-id="adf67-122">The XML Document Object Model (DOM) implementation guarantees that as long as this `book` element exists, it has these three default attributes of `att1`, `att2`, and `att3`.</span></span>  
  
 <span data-ttu-id="adf67-123">當使用 <xref:System.Xml.XmlAttribute> 呼叫時，<xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> 方法會將屬性值設為 String.Empty，因為屬性一定要有值。</span><span class="sxs-lookup"><span data-stu-id="adf67-123">When called with an <xref:System.Xml.XmlAttribute>, the <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> method sets the value of the attribute to String.Empty, as an attribute cannot exist without a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf67-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adf67-124">See also</span></span>

- [<span data-ttu-id="adf67-125">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="adf67-125">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
