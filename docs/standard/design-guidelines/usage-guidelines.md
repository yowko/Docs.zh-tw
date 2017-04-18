---
title: "用法方針 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "類別庫設計方針 [.NET Framework] 使用指導方針"
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 用法方針
本章節包含可公開存取的 Api 中使用一般類型的指導方針。 所以它處理直接使用內建 Framework 型別 （例如，序列化屬性） 和多載一般運算子。  
  
 <xref:System.IDisposable?displayProperty=fullName> 介面未涵蓋在本節中，但會討論 [處置模式](../../../docs/standard/design-guidelines/dispose-pattern.md) 一節。  
  
> [!NOTE]
>  指導方針和其他常見的相關其他相關資訊，內建的.NET Framework 型別，請參閱下列主題︰ <xref:System.DateTime?displayProperty=fullName>, ，<xref:System.DateTimeOffset?displayProperty=fullName>, ，<xref:System.ICloneable?displayProperty=fullName>, ，<xref:System.IComparable%601?displayProperty=fullName>, ，<xref:System.IEquatable%601?displayProperty=fullName>, ，<xref:System.Nullable%601?displayProperty=fullName>, ，<xref:System.Object?displayProperty=fullName>, ，<xref:System.Uri?displayProperty=fullName>。  
  
## 在本節中  
 [陣列](../../../docs/standard/design-guidelines/arrays.md)  
 [屬性](../../../docs/standard/design-guidelines/屬性.md)  
 [集合](../../../amples/snippets/cpp/VS_Snippets_Misc/cx_collections/cpp/collections.vcxproj)  
 [序列化](../../../docs/standard/design-guidelines/序列化.md)  
 [System.Xml 使用方式](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [等號比較運算子](../../../docs/standard/design-guidelines/equality-operators.md)  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)