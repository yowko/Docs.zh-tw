---
title: "列舉設計 | Microsoft Docs"
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
  - "類型設計方針，列舉型別"
  - "簡單列舉型別"
  - "列舉 [.NET Framework] 設計指導方針"
  - "類別庫設計方針 [.NET Framework] 列舉型別"
  - "旗標列舉型別"
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 列舉設計
列舉是特殊類型的實值型別。 有兩種類型的列舉︰ 簡單列舉和旗標的列舉。  
  
 簡單列舉代表小型關閉的選項集。 簡單列舉的常見範例是一組色彩。  
  
 旗標列舉被設計來支援的列舉值的位元運算。 旗標列舉的常見範例是選項的清單。  
  
 **✓ 執行** 列舉使用強型別參數、 屬性和傳回值，表示一組值。  
  
 **✓ 執行** 偏好使用列舉，而不靜態的常數。  
  
 **X 不** 列舉用於開啟集合 （例如作業系統版本、 名稱，您的朋友等等）。  
  
 **X 不** 保留的列舉值所提供供日後使用。  
  
 一律只是，您可以新增至現有的列舉值在稍後的階段。 請參閱 [加入列舉值](#add_value) 如需有關將值加入至列舉。 保留的值只 pollute 實際值的集合，通常會導致使用者錯誤。  
  
 **X 避免** 公開僅有一個值的列舉。  
  
 確保未來的擴充性的 C Api 的常見作法是將保留的參數加入至方法簽章。 這種保留的參數可以表示成單一的預設值的列舉。 這不應該在受管理的 Api。 方法多載，可新增參數在未來的版本。  
  
 **X 不** sentinel 值包含在列舉中。  
  
 雖然有時候很有幫助架構開發人員，sentinel 值可能會覺得混淆架構的使用者。 它們可用來追蹤狀態的列舉，而不是其中一個值是從列舉所代表的集。  
  
 **✓ 執行** 提供簡單列舉的零值。  
  
 請考慮呼叫值類似"None"。 如果這類值不適用於這個特定的列舉，最常用的預設值的列舉應該指派零的基礎值。  
  
 **✓ 考慮** 使用 <xref:System.Int32> （大部分的程式設計語言中的預設值） 做為列舉的基礎型別除非有下列情況︰  
  
-   列舉是旗標列舉，您有 32 個以上的旗標，或希望有更多的未來。  
  
-   基礎型別必須是不同於 <xref:System.Int32> 更輕鬆的互通性與 unmanaged 程式碼必須要有不同大小的列舉。  
  
-   小的基礎型別可能會導致大幅節省空間。 如果您希望列舉可用來主要是做為控制流程的引數，則大小將只有些微的差異。 省下的大小可能會很大如果︰  
  
    -   您會經常執行個體化的結構或類別中的欄位使用的列舉。  
  
    -   您預期使用者會建立大型陣列或集合的列舉執行個體。  
  
    -   您預期大量列舉要序列化的執行個體。  
  
 在 \[記憶體使用量和留意的受管理的物件永遠都 `DWORD`\-對齊，因此您實際上需要多個列舉或其他小型結構才能造成差異，組件與較小的列舉，因為總執行個體大小永遠都會四捨五入至執行個體中 `DWORD`。  
  
 **✓ 執行** 命名旗標列舉的複數名詞或名詞片語，並使用單數名詞或名詞片語的簡單列舉。  
  
 **X 不** 擴充 <xref:System.Enum?displayProperty=fullName> 直接。  
  
 <xref:System.Enum?displayProperty=fullName> 是一種特殊類型用於由 CLR 建立使用者定義的列舉型別。 大部分的程式設計語言提供可讓您存取這項功能的程式設計項目。 例如，在 C\# `enum` 關鍵字用來定義列舉型別。  
  
<a name="design"></a>   
### 設計旗標列舉  
 **✓ 執行** 套用 <xref:System.FlagsAttribute?displayProperty=fullName> 用於旗標列舉。 並用於簡單列舉適用這個屬性。  
  
 **✓ 執行** 使用乘冪數的旗標列舉值，所以它們也可以自由結合使用位元 OR 運算。  
  
 **✓ 考慮** 通常提供特殊的列舉值使用的旗標的組合。  
  
 位元運算是進階的概念，而且應該不需要簡單的工作。<xref:System.IO.FileAccess> 是特殊值的範例。  
  
 **X 避免** 建立旗標列舉值的特定組合的無效。  
  
 **X 避免** 值代表 「 清除所有旗標 」，並會適當地命名下, 一步的指導方針所規定除非使用旗標列舉值為零。  
  
 **✓ 執行** 旗標列舉的零值命名為 `None`。 對於旗標列舉值必須一律表示 「 清除所有旗標 」。  
  
<a name="add_value"></a>   
### 將值加入至列舉  
 它是很常見的作法會發現需要您具有已出貨之後，將值加入至列舉。 潛在的應用程式相容性問題時沒有新增的值會傳回從現有的 API，因為撰寫不夠周全的應用程式可能會正確處理新的值。  
  
 **✓ 考慮** 將值加入至列舉，儘管有小型的相容性的風險。  
  
 如果您有應用程式不相容的列舉新增項目所造成的相關的實際資料，請考慮加入新的 API，會傳回新的和舊值，並取代舊的 API，應該會繼續傳回舊的值。 這可確保您現有的應用程式保持相容。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)