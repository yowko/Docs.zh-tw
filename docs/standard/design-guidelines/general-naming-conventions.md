---
title: 一般命名慣例
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: d1b01fac7368ffeceb554c6f12aecb8f8760fa1d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709331"
---
# <a name="general-naming-conventions"></a>一般命名慣例
本節說明與 word 選擇相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及如何避免使用特定語言名稱的建議。  
  
## <a name="word-choice"></a>Word 選擇  
 **✓確實**要選擇容易閱讀的識別碼名稱。  
  
 例如，名為 `HorizontalAlignment` 的屬性比 `AlignmentHorizontal`更容易閱讀。  
  
 **✓**在簡潔的同時也偏好可讀性。  
  
 屬性名稱 `CanScrollHorizontally` 比 `ScrollableX` 更好（X 軸的模糊參考）。  
  
 **X 不會**使用底線、連字號或任何其他非英數位元。  
  
 **X**不使用匈牙利標記法。  
  
 **X 避免**使用與常用程式設計語言的關鍵字衝突的識別碼。  
  
 根據 Common Language Specification （CLS）的規則4，所有符合標準的語言都必須提供一種機制，允許存取使用該語言的關鍵字做為識別碼的命名專案。 C#例如，在此情況下，會使用 @ 符號做為 escape 機制。 不過，要避免使用一般關鍵字是個不錯的主意，因為在沒有此方法的情況下，您會比較難以使用具有 escape 序列的方法。  
  
## <a name="using-abbreviations-and-acronyms"></a>使用縮寫和縮略字  
 **X 不會**使用縮寫或縮寫做為識別碼名稱的一部分。  
  
 例如，使用 `GetWindow`，而不是 `GetWin`。  
  
 **X**不會使用未廣泛接受的任何縮略字，而且只會在必要時使用。  
  
## <a name="avoiding-language-specific-names"></a>避免語言特定的名稱  
 **✓確實**會使用語義上有趣的名稱，而不是類型名稱的特定語言關鍵字。  
  
 例如，`GetLength` 是比 `GetInt`更好的名稱。  
  
 在罕見的情況下， **✓確實**會使用泛型 CLR 型別名稱，而不是特定語言的名稱，但在少數情況下，識別碼沒有超出其型別的語義意義。  
  
 例如，轉換成 <xref:System.Int64> 的方法應該命名 `ToInt64`，而不是 `ToLong` （因為 <xref:System.Int64> 是特定別名 `long`的 CLR C#名稱）。 下表使用 CLR 型別名稱（以及、Visual Basic 和C# C++的對應型別名稱）來呈現數個基底資料類型。  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**Short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**布林值**|**bool**|**布林值**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**String**|**String**|**String**|  
|**object**|**物件**|**物件**|**物件**|  
  
 **✓確實**使用一般名稱，例如 `value` 或 `item`，而不是重複型別名稱，但在少數情況下，識別碼沒有語義意義，而參數的型別並不重要。  
  
## <a name="naming-new-versions-of-existing-apis"></a>命名現有 Api 的新版本  
 建立現有 API 的新版本時， **✓**會使用與舊 api 類似的名稱。  
  
 這有助於反白顯示 Api 之間的關聯性。  
  
 **✓**偏好新增尾碼，而不是前置詞，以表示現有 API 的新版本。  
  
 這有助於在流覽檔或使用 IntelliSense 時進行探索。 舊版的 API 會組織成接近新的 Api，因為大部分的瀏覽器和 IntelliSense 都會依字母順序顯示識別碼。  
  
 **✓請考慮**使用全新但有意義的識別碼，而不是新增尾碼或前置詞。  
  
 **✓**會使用數值尾碼來表示現有 api 的新版本，特別是當 api 的現有名稱是唯一可行的名稱時（亦即，如果它是業界標準），而且如果新增任何有意義的尾碼（或變更名稱）不是適當的選項。  
  
 **X 不會**使用識別碼的 "Ex" （或類似的）尾碼來區別它與舊版的相同 API。  
  
 當導入在64位整數（長整數）上運作的 Api 版本，而不是32位整數時， **✓確實**會使用 "64" 尾碼。 當現有的32位 API 存在時，您只需要採取此方法;請勿針對只有64位版本的全新 Api 執行此動作。  
  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
