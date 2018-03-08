---
title: "XML 型別支援實作注意事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8c2706782ed1242ecdb5af1fdfab7a3f24e19236
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="xml-type-support-implementation-notes"></a><span data-ttu-id="da0a1-102">XML 型別支援實作注意事項</span><span class="sxs-lookup"><span data-stu-id="da0a1-102">XML Type Support Implementation Notes</span></span>
<span data-ttu-id="da0a1-103">本主題說明一些您想要知道的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="da0a1-103">This topic describes some implementation details that you want to be aware of.</span></span>  
  
## <a name="list-mappings"></a><span data-ttu-id="da0a1-104">清單對應</span><span class="sxs-lookup"><span data-stu-id="da0a1-104">List Mappings</span></span>  
 <span data-ttu-id="da0a1-105"><xref:System.Collections.IList>、<xref:System.Collections.ICollection>、<xref:System.Collections.IEnumerable>、**Type[]** 及 <xref:System.String> 型別用於表示 XML 結構描述定義語言 (XSD) 清單型別。</span><span class="sxs-lookup"><span data-stu-id="da0a1-105">The <xref:System.Collections.IList>, <xref:System.Collections.ICollection>, <xref:System.Collections.IEnumerable>, **Type[]**, and <xref:System.String> types are used to represent XML Schema definition language (XSD) list types.</span></span>  
  
## <a name="union-mappings"></a><span data-ttu-id="da0a1-106">聯集對應</span><span class="sxs-lookup"><span data-stu-id="da0a1-106">Union Mappings</span></span>  
 <span data-ttu-id="da0a1-107">聯集型別是使用 <xref:System.Xml.Schema.XmlAtomicValue> 或 <xref:System.String> 型別來表示。</span><span class="sxs-lookup"><span data-stu-id="da0a1-107">Union types are represented using the <xref:System.Xml.Schema.XmlAtomicValue> or <xref:System.String> type.</span></span> <span data-ttu-id="da0a1-108">因此，來源型別或目的型別必須恆為 <xref:System.String> 或 <xref:System.Xml.Schema.XmlAtomicValue>。</span><span class="sxs-lookup"><span data-stu-id="da0a1-108">The source type or the destination type must therefore always be either <xref:System.String> or <xref:System.Xml.Schema.XmlAtomicValue>.</span></span>  
  
 <span data-ttu-id="da0a1-109">如果 <xref:System.Xml.Schema.XmlSchemaDatatype> 物件表示清單型別，則該物件會將輸入字串值轉換為一個或多個物件的清單。</span><span class="sxs-lookup"><span data-stu-id="da0a1-109">If the <xref:System.Xml.Schema.XmlSchemaDatatype> object represents a list type the object converts the input string value to a list of one or more objects.</span></span> <span data-ttu-id="da0a1-110">如果 <xref:System.Xml.Schema.XmlSchemaDatatype> 表示聯集型別，則會嘗試將輸入值剖析為聯集成員型別。</span><span class="sxs-lookup"><span data-stu-id="da0a1-110">If the <xref:System.Xml.Schema.XmlSchemaDatatype> represents a union type then an attempt is made to parse the input value as a member type of the union.</span></span> <span data-ttu-id="da0a1-111">如果剖析嘗試失敗，則會嘗試使用下一個聯集成員進行轉換，依此類推，直到轉換成功為止，或直到沒有其他可嘗試的成員型別為止，在此情況下會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da0a1-111">If the parse attempt fails then the conversion is attempted with the next member of the union and so on until the conversion is successful, or there are no other member types to try, in which case an exception is thrown.</span></span>  
  
## <a name="differences-between-clr-and-xml-data-types"></a><span data-ttu-id="da0a1-112">CLR 與 XML 資料型別之間的差異</span><span class="sxs-lookup"><span data-stu-id="da0a1-112">Differences Between CLR and XML Data Types</span></span>  
 <span data-ttu-id="da0a1-113">下列說明 CLR 型別與 XML 資料型別之間可能發生的某些不符狀況及其處理方式。</span><span class="sxs-lookup"><span data-stu-id="da0a1-113">The following describes certain mismatches that can occur between CLR types and XML data types and how they are handled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da0a1-114">`xs` 前置詞對應至 http://www.w3.org/2001/XMLSchema 及命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="da0a1-114">The `xs` prefix is mapped to the http://www.w3.org/2001/XMLSchema and namespace URI.</span></span>  
  
### <a name="systemtimespan-and-xsduration"></a><span data-ttu-id="da0a1-115">System.TimeSpan 及 xs:duration</span><span class="sxs-lookup"><span data-stu-id="da0a1-115">System.TimeSpan and xs:duration</span></span>  
 <span data-ttu-id="da0a1-116">`xs:duration` 型別為部分排序，因為有某些期間值雖不同但意義相當。</span><span class="sxs-lookup"><span data-stu-id="da0a1-116">The `xs:duration` type is partially ordered in that there are certain duration values that are different but equivalent.</span></span> <span data-ttu-id="da0a1-117">這表示對於 `xs:duration` 型別，值 1 個月 (P1M) 小於 32 天 (P32D)，大於 27 天 (P27D)，但等於 28、29 或 30 天。</span><span class="sxs-lookup"><span data-stu-id="da0a1-117">This means that for the `xs:duration` type value such as 1 month (P1M) is less than 32 days (P32D), larger than 27 days (P27D) and equivalent to 28, 29 or 30 days.</span></span>  
  
 <span data-ttu-id="da0a1-118"><xref:System.TimeSpan> 類別不支援這種部分排序。</span><span class="sxs-lookup"><span data-stu-id="da0a1-118">The <xref:System.TimeSpan> class does not support this partial ordering.</span></span> <span data-ttu-id="da0a1-119">而是會挑選特定的天數來表示 1 年及 1 個月；分別為 365 天及 30 天。</span><span class="sxs-lookup"><span data-stu-id="da0a1-119">Instead, it picks a specific number of days for 1 year and 1 month; 365 days and 30 days respectively.</span></span>  
  
 <span data-ttu-id="da0a1-120">如需 `xs:duration` 型別的詳細資訊，請參閱＜W3C XML 結構描述第二部：資料型別建議事項＞(英文)，網址是 http://www.w3.org/TR/xmlschema-2/。</span><span class="sxs-lookup"><span data-stu-id="da0a1-120">For more information on the `xs:duration` type, see the W3C XML Schema Part 2: Datatypes Recommendation at http://www.w3.org/TR/xmlschema-2/.</span></span>  
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a><span data-ttu-id="da0a1-121">xs:time (公曆日期型別) 及 System.DateTime</span><span class="sxs-lookup"><span data-stu-id="da0a1-121">xs:time, Gregorian Date Types, and System.DateTime</span></span>  
 <span data-ttu-id="da0a1-122">當 `xs:time` 值對應至 <xref:System.DateTime> 物件時，會使用 <xref:System.DateTime.MinValue> 欄位將 <xref:System.DateTime> 物件的日期屬性 (如 <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A> 及 <xref:System.DateTime.Day%2A>) 初始化為最小的 <xref:System.DateTime> 可能值。</span><span class="sxs-lookup"><span data-stu-id="da0a1-122">When an `xs:time` value is mapped to a <xref:System.DateTime> object, the <xref:System.DateTime.MinValue> field is used to initialize the date properties of the <xref:System.DateTime> object (such as <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, and <xref:System.DateTime.Day%2A>) to the smallest possible <xref:System.DateTime> value.</span></span>  
  
 <span data-ttu-id="da0a1-123">同樣地，`xs:gMonth`、`xs:gDay`、`xs:gYear`、`xs:gYearMonth` 及 `xs:gMonthDay` 的執行個體也對應至 <xref:System.DateTime> 物件。</span><span class="sxs-lookup"><span data-stu-id="da0a1-123">Similarly, instances of `xs:gMonth`, `xs:gDay`, `xs:gYear`, `xs:gYearMonth` and `xs:gMonthDay` are also mapped to a <xref:System.DateTime> object.</span></span> <span data-ttu-id="da0a1-124"><xref:System.DateTime> 物件上未使用的屬性會初始化為那些來自 <xref:System.DateTime.MinValue> 的值。</span><span class="sxs-lookup"><span data-stu-id="da0a1-124">Unused properties on the <xref:System.DateTime> object are initialized to those from <xref:System.DateTime.MinValue>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da0a1-125">當內容的型別為 <xref:System.DateTime.Year%2A?displayProperty=nameWithType> 時，無法依賴 `xs:gMonthDay` 值。</span><span class="sxs-lookup"><span data-stu-id="da0a1-125">You cannot rely on the <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value when the content is typed as `xs:gMonthDay`.</span></span> <span data-ttu-id="da0a1-126">在此情況下，<xref:System.DateTime.Year%2A?displayProperty=nameWithType> 值始終設為 1904。</span><span class="sxs-lookup"><span data-stu-id="da0a1-126">The <xref:System.DateTime.Year%2A?displayProperty=nameWithType> value is always set to 1904 in this case.</span></span>  
  
### <a name="xsanyuri-and-systemuri"></a><span data-ttu-id="da0a1-127">xs:anyURI 及 System.Uri</span><span class="sxs-lookup"><span data-stu-id="da0a1-127">xs:anyURI and System.Uri</span></span>  
 <span data-ttu-id="da0a1-128">當表示相對 URI 的 `xs:anyURI` 執行個體對應至 <xref:System.Uri> 時，<xref:System.Uri> 物件就不具有基底 URI。</span><span class="sxs-lookup"><span data-stu-id="da0a1-128">When an instance of `xs:anyURI` that represents a relative URI is mapped to a <xref:System.Uri>, the <xref:System.Uri> object does not have a base URI.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0a1-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="da0a1-129">See Also</span></span>  
 [<span data-ttu-id="da0a1-130">System.Xml 類別中的類型支援</span><span class="sxs-lookup"><span data-stu-id="da0a1-130">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
