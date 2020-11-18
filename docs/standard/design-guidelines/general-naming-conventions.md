---
title: 一般命名慣例
description: 使用與 word 選項相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及避免語言特定名稱的指引。
ms.date: 10/22/2008
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
ms.openlocfilehash: ff9efd40b630e8e25963b3d69b026feea2823ece
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821095"
---
# <a name="general-naming-conventions"></a>一般命名慣例

本節說明與 word 選項相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及如何避免使用特定語言名稱的建議。

## <a name="word-choice"></a>單字選擇
 ✔️選擇容易讀取的識別碼名稱。

 例如，名為的屬性 `HorizontalAlignment` 比更容易閱讀英文 `AlignmentHorizontal` 。

 ✔️的可讀性比簡潔。

 屬性名稱 `CanScrollHorizontally` 優於 `ScrollableX` (X 軸) 的模糊參考。

 ❌ 請勿使用底線、連字號或任何其他非英數位元。

 ❌ 請勿使用匈牙利文標記法。

 ❌ 避免使用與廣泛使用的程式設計語言關鍵字衝突的識別碼。

 根據 Common Language Specification (CLS) 的規則4，所有符合規範的語言都必須提供一種機制，以允許存取使用該語言關鍵字做為識別碼的命名專案。 例如，在此情況下，c # 會使用 @ 符號作為 escape 機制。 不過，最好避免常見的關鍵字，因為使用具有 escape 序列的方法比沒有它的方法更為困難。

## <a name="using-abbreviations-and-acronyms"></a>使用縮寫和縮寫
 ❌ 請勿使用縮寫或縮寫做為識別碼名稱的一部分。

 例如，使用 `GetWindow` 而不是 `GetWin` 。

 ❌ 請勿使用任何未被廣泛接受的縮寫，即使它們是，也可以在必要時使用。

## <a name="avoiding-language-specific-names"></a>避免 Language-Specific 名稱
 ✔️會使用語義上有趣的名稱，而不是類型名稱的特定語言關鍵字。

 例如，的 `GetLength` 名稱比更好 `GetInt` 。

 在罕見的情況下，當識別碼沒有任何語義意義超過其型別時，✔️請使用泛型 CLR 型別名稱，而不是特定語言的名稱。

 例如，轉換為的方法 <xref:System.Int64> 應該命名為 `ToInt64` ，而不 `ToLong` 是 (，因為 <xref:System.Int64> 是 c # 特定別名) 的 CLR 名稱 `long` 。 下表顯示使用 CLR 型別名稱 (的數個基底資料類型，以及 c #、Visual Basic 和 c + +) 的對應型別名稱。

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**位元組**|**unsigned char**|**位元組**|
|**short**|**短**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**整數**|**int**|**Int32**|
|**uint**|**UInt32**|**不帶正負號的整數**|**UInt32**|
|**long**|**Long**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**Double**|**double**|**Double**|
|**bool**|**布林值**|**bool**|**布林值**|
|**char**|**字元**|**wchar_t**|**字元**|
|**string**|**String**|**String**|**String**|
|**object**|**Object**|**Object**|**Object**|

 ✔️使用一般名稱（例如 `value` 或 `item` ），而不是重複型別名稱，但在少數情況下，當識別碼沒有語義意義，且參數的類型不重要時。

## <a name="naming-new-versions-of-existing-apis"></a>命名現有 Api 的新版本
 ✔️在建立現有 API 的新版本時，請使用類似舊 API 的名稱。

 這有助於強調 Api 之間的關聯性。

 ✔️想要新增尾碼，而不是前置詞，以表示現有 API 的新版本。

 這有助於在流覽檔或使用 IntelliSense 時進行探索。 舊版的 API 將會組織在接近新的 Api，因為大部分的瀏覽器和 IntelliSense 會依字母順序顯示識別碼。

 ✔️考慮使用全新但有意義的識別碼，而不是新增尾碼或前置詞。

 ✔️使用數位尾碼來指出現有 API 的新版本，尤其是當 API 的現有名稱是唯一 (合理的名稱時（例如，如果它是產業標準) ），而且如果新增任何有意義的尾碼 (或變更名稱) 則不是適當的選項。

 ❌ 請勿針對識別碼使用 "Ex" (或類似的) 尾碼，以區分它與舊版的相同 API。

 ✔️在導入在64位整數上運作的 Api 版本時，請使用 "64" 尾碼 (長整數) 而非32位整數。 當現有的32位 API 存在時，您只需要採取這種方法;請勿使用只有64位版本的全新 Api 來進行。

 *部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [Framework 設計方針](index.md)
- [命名方針](naming-guidelines.md)
- [EditorConfig 的 .NET 命名慣例](/visualstudio/ide/editorconfig-naming-conventions)
