---
title: "一般命名慣例 | Microsoft Docs"
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
  - "名稱 [.NET Framework] 衝突"
  - "型別名稱衝突"
  - "語言特定的類型名稱"
  - "關於命名方針名稱 [.NET Framework]"
  - "名稱 [.NET Framework] 縮寫"
  - "命名方針縮寫"
  - "命名方針縮略字"
  - "匈牙利文標記法"
  - "名稱 [.NET Framework] 的型別名稱"
  - "名稱 [.NET Framework] 首字母縮略字"
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 一般命名慣例
本章節描述一般命名慣例與 word 選擇使用縮寫首字母縮略字，並建議如何避免使用語言特定名稱的指導方針。  
  
## 字組選擇  
 **✓ 執行** 選擇簡單易讀的識別項名稱。  
  
 例如，名為的屬性 `HorizontalAlignment` 是英文\-可讀性比 `AlignmentHorizontal`。  
  
 **✓ 執行** 優先求簡單明瞭的可讀性。  
  
 屬性名稱 `CanScrollHorizontally` 優於 `ScrollableX` （x 軸難以理解參考）。  
  
 **X 不** 使用底線、 連字號或任何其他非英數字元。  
  
 **X 不** 使用匈牙利標記法。  
  
 **X 避免** 使用廣泛使用的關鍵字衝突的識別項使用的程式設計語言。  
  
 根據規則 4 的 Common Language Specification \(CLS\) 中，所有相容的語言必須提供一種機制，可讓使用該語言的關鍵字當做識別項的具名項目的存取權。 C\# 中，例如，使用 @ 符號做為逸出機制，在此情況下。 然而，仍然是個不錯的主意，避免常用的關鍵字，因為它是比另一個則不逸出序列使用的方法更困難。  
  
## 使用縮寫和縮略字  
 **X 不** 縮寫或縮減做為識別項名稱的一部分。  
  
 例如，使用 `GetWindow` 而 `GetWin`。  
  
 **X 不** 使用廣泛被接受，甚至還能如有需要，只在必要時，不是任何縮略字。  
  
## 避免特定語言的名稱  
 **✓ 執行** 語意方面有意義的名稱，而不是語言特有的關鍵字用於型別名稱。  
  
 例如， `GetLength` 是更好的名稱，比 `GetInt`。  
  
 **✓ 執行** 罕見的情況下，在識別項不具有任何語意超出其型別時使用泛型的 CLR 型別名稱，而不是特定語言的名稱。  
  
 例如，將轉換成方法 <xref:System.Int64> 命名為 `ToInt64`, ，而非 `ToLong` \(因為 <xref:System.Int64> 是 C\# 的 CLR 名稱\-特定別名 `long`\)。 下表顯示使用的 CLR 型別名稱 （以及對應的型別名稱，如 C\#、 Visual Basic 和 c \+ \+） 的數個基底資料型別。  
  
|C\#|Visual Basic|C\+\+|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**簡短**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**\_\_int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned \_\_int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Boolean**|**bool**|**Boolean**|  
|**char**|**Char**|**wchar\_t**|**Char**|  
|**string**|**String**|**String**|**String**|  
|**object**|**物件**|**物件**|**物件**|  
  
 **✓ 執行**  使用一般名稱，例如 `value` 或 `item`, ，而不是重複的型別名稱，在少數情況下，當識別項具有任何語意和參數的型別並不重要。  
  
## 命名新版本的現有 Api  
 **✓ 執行** 建立新版本的現有 API 時使用的舊的 API 類似的名稱。  
  
 這有助於反白顯示 Api 之間的關聯性。  
  
 **✓ 執行** 偏好新增後置詞，而非前置詞來表示現有 api 的新版本。  
  
 瀏覽文件時，這樣可以幫助探索或使用 Intellisense。 將新的 Api，接近組織舊版本的 API，因為大部分的瀏覽器和 Intellisense 會依字母順序顯示識別項。  
  
 **✓ 考慮** 使用全新、 但有意義的識別項，而不要新增後置字元或前置詞。  
  
 **✓ 執行** 用於數值後置詞表示現有 API 的新版本，尤其是現有 API 的名稱是唯一的名稱 （亦即，如果它是一種業界標準） 具有意義的如果加入任何有意義尾碼 （或變更名稱） 不適當的選項。  
  
 **X 不** 使用 「 Ex 」 （或類似） 後置詞，以區分它與舊版相同的 API 的識別項。  
  
 **✓ 執行** 導入的 Api，而不是 32 位元整數的 64 位元整數 \(long\) 上運作的版本時，會使用"64"尾碼。 您只需要採用這種方法，當現有的 32 位元 API 存在。不要這麼做以 64 位元版本的全新 api。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)