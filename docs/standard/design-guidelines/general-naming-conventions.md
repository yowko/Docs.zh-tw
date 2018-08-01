---
title: 一般命名慣例
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 207227b3e5c52b7c6e0f704543379874f3708c03
ms.sourcegitcommit: ceca5a1c027627abcca2767567703c3879f33325
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2018
ms.locfileid: "36338100"
---
# <a name="general-naming-conventions"></a>一般命名慣例
本章節描述一般命名慣例與相關單字的選擇，如何避免使用特定語言的名稱中使用縮寫和首字母縮略字和建議的指導方針。  
  
## <a name="word-choice"></a>字組選擇  
 **✓ DO**選擇簡單易讀的識別項名稱。  
  
 例如，名為的屬性`HorizontalAlignment`是英文-可讀性比`AlignmentHorizontal`。  
  
 **✓ DO**勝過求簡單明瞭的可讀性。  
  
 屬性名稱`CanScrollHorizontally`優於`ScrollableX`（x 軸之下參考）。  
  
 **X DO NOT**使用底線、 連字號或任何其他非英數字元。  
  
 **X DO NOT**使用匈牙利標記法。  
  
 **X AVOID**使用廣泛發生衝突之關鍵字的識別項使用的程式設計語言。  
  
 根據規則 4 的 Common Language Specification (CLS) 中，所有相容的語言必須提供一套機制，可讓使用該語言的關鍵字當做識別項的具名項目的存取權。 C# 中，例如，使用 @ 符號做為逸出機制，在此情況下。 不過，它仍然是個不錯的主意，避免常見的關鍵字，因為它是使用比另一個則不逸出序列使用的方法更為困難。  
  
## <a name="using-abbreviations-and-acronyms"></a>使用縮寫和縮略字  
 **X DO NOT**縮寫做為識別項名稱的一部分。  
  
 例如，使用`GetWindow`而不是`GetWin`。  
  
 **X DO NOT**使用任何不是普遍被接受，且即使它們是，只在必要時的縮略字。  
  
## <a name="avoiding-language-specific-names"></a>避免將語言特定名稱  
 **✓ DO**語意方面有意義的名稱，而不是語言特有的關鍵字用於型別名稱。  
  
 例如，`GetLength`是更適合的名稱，比`GetInt`。  
  
 **✓ DO**使用泛型的 CLR 型別名稱，而非語言特定名稱，在極少數的情況下，當識別項不具有任何超出其類型的語意。  
  
 例如，將轉換成方法<xref:System.Int64>應命名為`ToInt64`，而非`ToLong`(因為<xref:System.Int64>是 C# 的 CLR 名稱-特定別名`long`)。 下表顯示使用 CLR 型別名稱 （以及對應的型別名稱，如 C#、 Visual Basic 和 c + +） 的數個基底資料類型。  
  
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
  
 **✓ DO**使用一般名稱，例如`value`或`item`，而不是重複的型別名稱，在極少數的情況下，當識別項具有任何語意和參數的型別並不重要。  
  
## <a name="naming-new-versions-of-existing-apis"></a>命名新版本的現有應用程式開發介面  
 **✓ DO**建立新版本的現有應用程式開發介面時，使用舊的 API 類似的名稱。  
  
 這有助於反白顯示的應用程式開發介面之間的關聯性。  
  
 **✓ DO**偏好加入後置詞，而不是前置詞，指示現有的應用程式開發介面的新版本。  
  
 瀏覽文件時，這將可協助探索或使用 IntelliSense。 將新的 Api，接近組織 API 的舊版本，因為大部分的瀏覽器和 IntelliSense 會依字母順序顯示識別項。  
  
 **✓ CONSIDER**使用全新，但有意義的識別項，而非新增後置字元或前置詞。  
  
 **✓ DO**使用數值後置詞表示新版本的現有應用程式開發介面，尤其是如果現有的 API 名稱是唯一的名稱 （亦即，如果它是一種業界標準） 有意義且如果加入任何有意義尾碼 （或變更名稱） 不是應用程式ropriate 選項。  
  
 **X DO NOT**使用"Ex"（或類似） 後置字元加以區別較早版本的相同應用程式開發介面識別項。  
  
 **✓ DO**簡介操作的 64 位元整數 （長整數），而不是 32 位元整數的 Api 版本時，使用"64"後置詞。 您只需要存在現有的 32 位元應用程式開發介面; 時採取這種方式不要做為 64 位元版本的全新 Api。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
