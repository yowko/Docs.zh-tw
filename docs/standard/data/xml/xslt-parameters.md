---
title: "XSLT 參數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e66d98501bb0bd3a5d5cd5eacc0b09405c158522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="xslt-parameters"></a><span data-ttu-id="27170-102">XSLT 參數</span><span class="sxs-lookup"><span data-stu-id="27170-102">XSLT Parameters</span></span>
<span data-ttu-id="27170-103">XSLT 參數可使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法加入至 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>。</span><span class="sxs-lookup"><span data-stu-id="27170-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="27170-104">限定名稱與命名空間 URI 會在此時與參數物件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="27170-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="27170-105">使用 XSLT 參數</span><span class="sxs-lookup"><span data-stu-id="27170-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="27170-106">建立 <xref:System.Xml.Xsl.XsltArgumentList> 物件，並使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法加入參數。</span><span class="sxs-lookup"><span data-stu-id="27170-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="27170-107">從樣式表呼叫參數。</span><span class="sxs-lookup"><span data-stu-id="27170-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="27170-108">將 <xref:System.Xml.Xsl.XsltArgumentList> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="27170-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="27170-109">參數型別</span><span class="sxs-lookup"><span data-stu-id="27170-109">Parameter Types</span></span>  
 <span data-ttu-id="27170-110">參數物件應對應至 W3C 型別。</span><span class="sxs-lookup"><span data-stu-id="27170-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="27170-111">下表顯示對應的 W3C 型別、對等的 Microsoft .NET 類別 (型別)，以及 W3C 型別是 XPath 型別還是 XSLT 型別。</span><span class="sxs-lookup"><span data-stu-id="27170-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="27170-112">W3C 類型</span><span class="sxs-lookup"><span data-stu-id="27170-112">W3C type</span></span>|<span data-ttu-id="27170-113">對等的 .NET 類別 (型別)</span><span class="sxs-lookup"><span data-stu-id="27170-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="27170-114">XPath 或 XSLT 型別</span><span class="sxs-lookup"><span data-stu-id="27170-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="27170-115">XPath</span><span class="sxs-lookup"><span data-stu-id="27170-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="27170-116">XPath</span><span class="sxs-lookup"><span data-stu-id="27170-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="27170-117">XPath</span><span class="sxs-lookup"><span data-stu-id="27170-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="27170-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="27170-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="27170-119">XPath</span><span class="sxs-lookup"><span data-stu-id="27170-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="27170-120">**XPathNavigator]**</span><span class="sxs-lookup"><span data-stu-id="27170-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="27170-121">XPath</span><span class="sxs-lookup"><span data-stu-id="27170-121">XPath</span></span>|  
  
 <span data-ttu-id="27170-122">*這相當於含有單一節點的節點集。</span><span class="sxs-lookup"><span data-stu-id="27170-122">*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="27170-123">如果參數物件不是上述其中一個類別，則會根據下列規則進行轉換。</span><span class="sxs-lookup"><span data-stu-id="27170-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="27170-124">Common Language Runtime (CLR) 數字型別會轉換為 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="27170-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="27170-125"><xref:System.DateTime> 類型會轉換為 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="27170-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="27170-126"><xref:System.Xml.XPath.IXPathNavigable> 類型會轉換為 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="27170-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="27170-127">**XPathNavigator []**轉換成<xref:System.Xml.XPath.XPathNodeIterator>。</span><span class="sxs-lookup"><span data-stu-id="27170-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="27170-128">所有其他類型都會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="27170-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27170-129">範例</span><span class="sxs-lookup"><span data-stu-id="27170-129">Example</span></span>  
 <span data-ttu-id="27170-130">下列範例將使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法，建立保留計算折扣日期的參數。</span><span class="sxs-lookup"><span data-stu-id="27170-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="27170-131">折扣日期計算為從訂購日期起的 20 天。</span><span class="sxs-lookup"><span data-stu-id="27170-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="27170-132">輸入</span><span class="sxs-lookup"><span data-stu-id="27170-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="27170-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="27170-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="27170-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="27170-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="27170-135">輸出</span><span class="sxs-lookup"><span data-stu-id="27170-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27170-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27170-136">See Also</span></span>  
 [<span data-ttu-id="27170-137">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="27170-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
