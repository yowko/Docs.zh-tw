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
ms.openlocfilehash: c90987fd28d5157cfb7f7eea4680b5ab4be1a200
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290950"
---
# <a name="general-naming-conventions"></a>一般命名慣例

本節說明與 word 選擇相關的一般命名慣例、使用縮寫和縮略字的指導方針，以及如何避免使用特定語言名稱的建議。

## <a name="word-choice"></a>Word 選擇
 ✔️選擇容易閱讀的識別碼名稱。

 例如，名為的屬性 `HorizontalAlignment` 比更具英文易懂 `AlignmentHorizontal` 。

 ✔️比簡單明瞭更方便閱讀。

 屬性名稱 `CanScrollHorizontally` 優於 `ScrollableX` （X 軸的模糊參考）。

 ❌請勿使用底線、連字號或任何其他非英數位元。

 ❌請勿使用匈牙利文標記法。

 ❌避免使用與常用程式設計語言的關鍵字衝突的識別碼。

 根據 Common Language Specification （CLS）的規則4，所有符合標準的語言都必須提供一種機制，允許存取使用該語言的關鍵字做為識別碼的命名專案。 例如，c # 在此情況下會使用 @ 符號做為 escape 機制。 不過，要避免使用一般關鍵字是個不錯的主意，因為在沒有此方法的情況下，您會比較難以使用具有 escape 序列的方法。

## <a name="using-abbreviations-and-acronyms"></a>使用縮寫和縮略字
 ❌請勿使用縮寫或縮寫做為識別碼名稱的一部分。

 例如，使用， `GetWindow` 而不是 `GetWin` 。

 ❌請勿使用未廣泛接受的任何縮略字，甚至是必要時，

## <a name="avoiding-language-specific-names"></a>避免語言特定的名稱
 ✔️確實會使用語義上有趣的名稱，而不是類型名稱的特定語言關鍵字。

 例如，的 `GetLength` 名稱比更好 `GetInt` 。

 ✔️確實使用泛型 CLR 型別名稱，而不是特定語言的名稱，但在少數情況下，識別碼沒有超出其型別的語義意義。

 例如，轉換成的方法 <xref:System.Int64> 應該命名為 `ToInt64` ，而不是 `ToLong` （因為 <xref:System.Int64> 是 c # 特定別名的 CLR 名稱 `long` ）。 下表會使用 CLR 型別名稱（以及 c #、Visual Basic 和 c + + 的對應型別名稱）來呈現數個基底資料類型。

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**節**|**unsigned char**|**節**|
|**short**|**短缺**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**介於**|**int**|**Int32**|
|**uint**|**UInt32**|**不帶正負號的整數**|**UInt32**|
|**long**|**Long**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**float**|**Single**|**float**|**Single**|
|**double**|**兩**|**double**|**兩**|
|**bool**|**Boolean**|**bool**|**Boolean**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**String**|**String**|**String**|
|**object**|**Object**|**Object**|**Object**|

 ✔️確實使用一般名稱，例如 `value` 或 `item` ，而不是重複型別名稱，但在少數情況下，識別碼沒有語義意義，且參數的型別不重要。

## <a name="naming-new-versions-of-existing-apis"></a>命名現有 Api 的新版本
 ✔️在建立現有 API 的新版本時，請使用與舊 API 類似的名稱。

 這有助於反白顯示 Api 之間的關聯性。

 ✔️偏好新增尾碼，而不是前置詞，以表示現有 API 的新版本。

 這有助於在流覽檔或使用 IntelliSense 時進行探索。 舊版的 API 會組織成接近新的 Api，因為大部分的瀏覽器和 IntelliSense 都會依字母順序顯示識別碼。

 ✔️考慮使用全新但有意義的識別碼，而不是新增尾碼或前置詞。

 ✔️確實使用數值尾碼來表示現有 API 的新版本，特別是當 API 的現有名稱是唯一有意義的名稱時（亦即，如果它是業界標準），而且如果新增任何有意義的尾碼（或變更名稱）不是適當的選項。

 ❌請不要將 "Ex" （或類似的）尾碼用於識別碼，以便與相同 API 的舊版進行區別。

 當導入在64位整數（長整數）上運作的 Api 版本，而不是32位整數時，✔️確實使用 "64" 尾碼。 當現有的32位 API 存在時，您只需要採取此方法;請勿針對只有64位版本的全新 Api 執行此動作。

 *部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](index.md)
- [命名方針](naming-guidelines.md)
- [EditorConfig 的 .NET 命名慣例](/visualstudio/ide/editorconfig-naming-conventions)
