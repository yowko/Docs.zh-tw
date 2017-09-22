---
title: "如何：在舊版編碼方式和 Unicode 間轉換 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], legacy to unicode encoding
- strings [C#], converting between encodings
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a016f4ab7de25eec408243cb9b467f9255556bba
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a>如何：在舊版編碼方式和 Unicode 間轉換 (C# 程式設計手冊)
在 C# 中，記憶體中的所有字串都編碼為 Unicode (UTF-16)。 當您將資料從儲存體送入 `string` 物件後，該資料就會自動轉換為 UTF-16。 如果資料只包含從 0 到 127 的 ASCII 值，您就不需要為轉換出任何力。 但若原始程式文字包含擴充的 ASCII 位元組值 (128 到 255)，擴充字元預設會根據目前的字碼頁解譯。 若要指定原始程式文字應根據不同的字碼頁解譯，請使用 <xref:System.Text.Encoding?displayProperty=fullName> 類別，如下列範例所示。  
  
## <a name="example"></a>範例  
 下列範例會示範如何根據 Windows 字碼頁 737 解譯原始程式文字，轉換已使用 8 位元 ASCII 編碼的文字檔。  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [字串](../../../csharp/programming-guide/strings/index.md)

