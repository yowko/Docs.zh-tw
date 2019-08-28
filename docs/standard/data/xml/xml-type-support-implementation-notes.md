---
title: XML 型別支援實作注意事項
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 26b071f3-1261-47ef-8690-0717f5cd93c1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 817d48e15f3a1d370e1953ca9c9aa8e10baa7f29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916038"
---
# <a name="xml-type-support-implementation-notes"></a>XML 型別支援實作注意事項
本主題說明一些您想要知道的實作詳細資料。  
  
## <a name="list-mappings"></a>清單對應  
 <xref:System.Collections.IList>、<xref:System.Collections.ICollection>、<xref:System.Collections.IEnumerable>、**Type[]** 及 <xref:System.String> 型別用於表示 XML 結構描述定義語言 (XSD) 清單型別。  
  
## <a name="union-mappings"></a>聯集對應  
 聯集型別是使用 <xref:System.Xml.Schema.XmlAtomicValue> 或 <xref:System.String> 型別來表示。 因此，來源型別或目的型別必須恆為 <xref:System.String> 或 <xref:System.Xml.Schema.XmlAtomicValue>。  
  
 如果 <xref:System.Xml.Schema.XmlSchemaDatatype> 物件表示清單型別，則該物件會將輸入字串值轉換為一個或多個物件的清單。 如果 <xref:System.Xml.Schema.XmlSchemaDatatype> 表示聯集型別，則會嘗試將輸入值剖析為聯集成員型別。 如果剖析嘗試失敗，則會嘗試使用下一個聯集成員進行轉換，依此類推，直到轉換成功為止，或直到沒有其他可嘗試的成員型別為止，在此情況下會擲回例外狀況。  
  
## <a name="differences-between-clr-and-xml-data-types"></a>CLR 與 XML 資料型別之間的差異  
 下列說明 CLR 型別與 XML 資料型別之間可能發生的某些不符狀況及其處理方式。  
  
> [!NOTE]
> `xs` 前置詞對應至 <https://www.w3.org/2001/XMLSchema> 和命名空間 URI。
  
### <a name="systemtimespan-and-xsduration"></a>System.TimeSpan 及 xs:duration  
 `xs:duration` 型別為部分排序，因為有某些期間值雖不同但意義相當。 這表示對於 `xs:duration` 型別，值 1 個月 (P1M) 小於 32 天 (P32D)，大於 27 天 (P27D)，但等於 28、29 或 30 天。  
  
 <xref:System.TimeSpan> 類別不支援這種部分排序。 而是會挑選特定的天數來表示 1 年及 1 個月；分別為 365 天及 30 天。  
  
 如需 `xs:duration` 類型的詳細資訊，請參閱 W3C [XML Schema Part 2:Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/) (XML 結構描述第 2 部分：資料類型建議)。
  
### <a name="xstime-gregorian-date-types-and-systemdatetime"></a>xs:time (公曆日期型別) 及 System.DateTime  
 當 `xs:time` 值對應至 <xref:System.DateTime> 物件時，會使用 <xref:System.DateTime.MinValue> 欄位將 <xref:System.DateTime> 物件的日期屬性 (如 <xref:System.DateTime.Year%2A>、<xref:System.DateTime.Month%2A> 及 <xref:System.DateTime.Day%2A>) 初始化為最小的 <xref:System.DateTime> 可能值。  
  
 同樣地，`xs:gMonth`、`xs:gDay`、`xs:gYear`、`xs:gYearMonth` 及 `xs:gMonthDay` 的執行個體也對應至 <xref:System.DateTime> 物件。 <xref:System.DateTime> 物件上未使用的屬性會初始化為那些來自 <xref:System.DateTime.MinValue> 的值。  
  
> [!NOTE]
> 當內容的型別為 <xref:System.DateTime.Year%2A?displayProperty=nameWithType> 時，無法依賴 `xs:gMonthDay` 值。 在此情況下，<xref:System.DateTime.Year%2A?displayProperty=nameWithType> 值始終設為 1904。  
  
### <a name="xsanyuri-and-systemuri"></a>xs:anyURI 及 System.Uri  
 當表示相對 URI 的 `xs:anyURI` 執行個體對應至 <xref:System.Uri> 時，<xref:System.Uri> 物件就不具有基底 URI。  
  
## <a name="see-also"></a>另請參閱

- [System.Xml 類別中的類型支援](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)
