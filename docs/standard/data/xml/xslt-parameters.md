---
title: XSLT 參數
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282528"
---
# <a name="xslt-parameters"></a><span data-ttu-id="f91e2-102">XSLT 參數</span><span class="sxs-lookup"><span data-stu-id="f91e2-102">XSLT Parameters</span></span>
<span data-ttu-id="f91e2-103">XSLT 參數可使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法加入至 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>。</span><span class="sxs-lookup"><span data-stu-id="f91e2-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="f91e2-104">限定名稱與命名空間 URI 會在此時與參數物件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="f91e2-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="f91e2-105">使用 XSLT 參數</span><span class="sxs-lookup"><span data-stu-id="f91e2-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="f91e2-106">建立 <xref:System.Xml.Xsl.XsltArgumentList> 物件，並使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法加入參數。</span><span class="sxs-lookup"><span data-stu-id="f91e2-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="f91e2-107">從樣式表呼叫參數。</span><span class="sxs-lookup"><span data-stu-id="f91e2-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="f91e2-108">將 <xref:System.Xml.Xsl.XsltArgumentList> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="f91e2-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="f91e2-109">參數型別</span><span class="sxs-lookup"><span data-stu-id="f91e2-109">Parameter Types</span></span>  
 <span data-ttu-id="f91e2-110">參數物件應對應至 W3C 型別。</span><span class="sxs-lookup"><span data-stu-id="f91e2-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="f91e2-111">下表顯示對應的 W3C 型別、對等的 Microsoft .NET 類別 (型別)，以及 W3C 型別是 XPath 型別還是 XSLT 型別。</span><span class="sxs-lookup"><span data-stu-id="f91e2-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="f91e2-112">W3C 類型</span><span class="sxs-lookup"><span data-stu-id="f91e2-112">W3C type</span></span>|<span data-ttu-id="f91e2-113">對等的 .NET 類別 (型別)</span><span class="sxs-lookup"><span data-stu-id="f91e2-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="f91e2-114">XPath 或 XSLT 型別</span><span class="sxs-lookup"><span data-stu-id="f91e2-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="f91e2-115">XPath</span><span class="sxs-lookup"><span data-stu-id="f91e2-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="f91e2-116">XPath</span><span class="sxs-lookup"><span data-stu-id="f91e2-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="f91e2-117">XPath</span><span class="sxs-lookup"><span data-stu-id="f91e2-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="f91e2-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="f91e2-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="f91e2-119">XPath</span><span class="sxs-lookup"><span data-stu-id="f91e2-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="f91e2-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="f91e2-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="f91e2-121">XPath</span><span class="sxs-lookup"><span data-stu-id="f91e2-121">XPath</span></span>|  
  
 <span data-ttu-id="f91e2-122">\*這相當於含有單一節點的節點集。</span><span class="sxs-lookup"><span data-stu-id="f91e2-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="f91e2-123">如果參數物件不是上述其中一個類別，則會根據下列規則進行轉換。</span><span class="sxs-lookup"><span data-stu-id="f91e2-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="f91e2-124">Common Language Runtime (CLR) 數字型別會轉換為 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="f91e2-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="f91e2-125"><xref:System.DateTime> 類型會轉換為 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="f91e2-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="f91e2-126"><xref:System.Xml.XPath.IXPathNavigable> 類型會轉換為 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="f91e2-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="f91e2-127">**XPathNavigator[]** 會轉換為 <xref:System.Xml.XPath.XPathNodeIterator>。</span><span class="sxs-lookup"><span data-stu-id="f91e2-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="f91e2-128">所有其他類型都會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="f91e2-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f91e2-129">範例</span><span class="sxs-lookup"><span data-stu-id="f91e2-129">Example</span></span>  
 <span data-ttu-id="f91e2-130">下列範例將使用 <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> 方法，建立保留計算折扣日期的參數。</span><span class="sxs-lookup"><span data-stu-id="f91e2-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="f91e2-131">折扣日期計算為從訂購日期起的 20 天。</span><span class="sxs-lookup"><span data-stu-id="f91e2-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="f91e2-132">輸入</span><span class="sxs-lookup"><span data-stu-id="f91e2-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="f91e2-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="f91e2-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="f91e2-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="f91e2-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="f91e2-135">輸出</span><span class="sxs-lookup"><span data-stu-id="f91e2-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f91e2-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f91e2-136">See also</span></span>

- [<span data-ttu-id="f91e2-137">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="f91e2-137">XSLT Transformations</span></span>](xslt-transformations.md)
