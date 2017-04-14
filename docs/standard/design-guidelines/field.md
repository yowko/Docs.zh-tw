---
title: "欄位設計 | Microsoft Docs"
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
  - "欄位中，設計方針"
  - "唯讀欄位"
  - "成員設計方針欄位"
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 欄位設計
封裝原則將其中一個最重要的概念是物件導向設計中。 此原則就是儲存在物件內的資料必須能夠存取只適用於該物件。  
  
 有用的方式來解譯原則是說應該設計為型別，以便該型別 （名稱或型別變更） 的欄位可以變更而不會中斷程式碼以外之成員的型別。 此解譯立即意味著所有欄位必須都是私用。  
  
 我們常數和靜態唯讀欄位從排除這個嚴格的限制，因為這類欄位，根據定義，幾乎永遠不需要變更。  
  
 **X 不** 提供公用或受保護的執行個體欄位。  
  
 您應該提供屬性來存取欄位，而不是公用或受保護，使它們。  
  
 **✓ 執行** 使用常數欄位的常數，永遠不會變更。  
  
 編譯器會燒壞常數欄位的值，直接在呼叫程式碼。 因此，常數值可以永遠不會變更而不中斷的相容性的風險。  
  
 **✓ 執行** 使用公用靜態 `readonly` 預先定義的物件執行個體的欄位。  
  
 如果有預先定義的類型執行個體，請將它們宣告為公用唯讀靜態欄位的型別本身。  
  
 **X 不** 指派到可變動型別的執行個體 `readonly` 欄位。  
  
 可變動類型是可以修改它們會具現化後的執行個體的類型。 例如，陣列、 大多數的集合，以及資料流是可變動的型別，但 <xref:System.Int32?displayProperty=fullName>, ，<xref:System.Uri?displayProperty=fullName>, ，和 <xref:System.String?displayProperty=fullName> 全都是不變。 參考型別欄位上的唯讀修飾詞會防止從已經被取代，欄位中儲存的執行個體，但它無法防止未變更的執行個體的呼叫成員的修改欄位的執行個體資料。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)