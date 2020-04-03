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
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635911"
---
# <a name="general-naming-conventions"></a>一般命名慣例

本節介紹與單詞選擇相關的一般命名約定、有關使用縮寫和首字母縮略詞的指南,以及如何避免使用特定於語言的名稱的建議。

## <a name="word-choice"></a>字選擇
 ✔️選擇易於讀的標識符名稱。

 例如,名為的屬性`HorizontalAlignment`比`AlignmentHorizontal`更具英語可讀性。

 ✔️確實傾向於可讀性而不是簡潔性。

 屬性名稱`CanScrollHorizontally`優`ScrollableX`於 (對 X 軸的模糊引用)。

 ❌請勿使用下劃線、連字元或任何其他非字母數位字元。

 ❌請勿使用匈牙利符號。

 ❌使用與廣泛使用的程式設計語言的關鍵字衝突的標識碼。

 根據通用語言規範 (CLS) 的規則 4,所有相容的語言都必須提供一種機制,允許存取使用該語言的關鍵字作為識別碼的命名項。 例如,在這種情況下,C# 使用 + 符號作為轉義機制。 但是,最好避免使用常見關鍵字,因為使用具有轉義序列的方法比沒有它的方法要困難得多。

## <a name="using-abbreviations-and-acronyms"></a>使用縮寫和縮圖
 ❌請勿將縮寫或縮略用作標識符名稱的一部分。

 例如,使用`GetWindow`而不是`GetWin`。

 ❌不要使用任何未被廣泛接受的首字母縮略詞,即使它們是,也不得在必要時使用。

## <a name="avoiding-language-specific-names"></a>避免特定於語言的名稱
 ✔️使用語義上有趣的名稱,而不是特定於語言的關鍵字來輸入類型名稱。

 例如,`GetLength``GetInt`比越好的名稱。

 ✔️ DO 使用泛型 CLR 類型名稱,而不是特定於語言的名稱,在標識符在其類型之外沒有語義含義的極少數情況下。

 例如,轉換<xref:System.Int64>到的方法應命名為`ToInt64`,`ToLong`而不是<xref:System.Int64>(因為是特定於 C#`long`的別名的 CLR 名稱)。 下表使用 CLR 類型名稱(以及 C#、Visual Basic 和C++的相應類型名稱)提供了幾種基本數據類型。

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**位元組**|**unsigned char**|**位元組**|
|**short**|**短**|**short**|**Int16**|
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|
|**int**|**整數**|**int**|**Int32**|
|**uint**|**UInt32**|**不帶正負號的整數**|**UInt32**|
|**長**|**Long**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|
|**浮動**|**單**|**浮動**|**單**|
|**double**|**雙**|**double**|**雙**|
|**bool**|**布林**|**bool**|**布林**|
|**char**|**字元**|**wchar_t**|**字元**|
|**string**|**字串**|**字串**|**字串**|
|**物件**|**Object**|**Object**|**Object**|

 ✔️ DO 使用公共名稱`value``item`,如或 ,而不是重複類型名稱,在標識符沒有語義含義且參數類型並不重要的罕見情況下。

## <a name="naming-new-versions-of-existing-apis"></a>命名現有 API 的新版本
 ✔️在現有 API 的新版本創建時,請使用與舊 API 類似的名稱。

 這有助於突出顯示 API 之間的關係。

 ✔️喜歡添加後綴而不是首碼來指示現有 API 的新版本。

 這將有助於在瀏覽文件或使用 IntelliSense 時發現。 API 的舊版本將組織在新 API 附近,因為大多數瀏覽器和 IntelliSense 都按字母順序顯示識別碼。

 ✔️考慮使用全新但有意義的標識符,而不是添加後綴或前綴。

 ✔️使用數位後綴來指示現有 API 的新版本,特別是如果 API 的現有名稱是唯一有意義的名稱(即,如果它是行業標準),並且添加任何有意義的後綴(或更改名稱)不是適當的選項。

 ❌請勿使用標識碼的「Ex」(或類似)後綴來區分它與同一 API 的早期版本。

 ✔️在引入使用 64 位整數(長整數)而不是 32 位整數的 API 版本時,請使用"64"後綴。 僅當存在現有的 32 位 API 時,才需要採用此方法;不要為只有 64 位元版本的全新 API 執行此操作。

 *部分&copy;2005, 2009 微軟公司.保留所有權利。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [具向指南](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [EditorConfig 的 .NET 命名慣例](/visualstudio/ide/editorconfig-naming-conventions)
