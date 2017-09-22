---
title: "如何：在 C# 中定義常數"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: 7
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
ms.openlocfilehash: 6c5a6f63675893eb0700afab462bf237f5639d74
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-constants-in-c"></a>如何：在 C# 中定義常數
常數是欄位，其值於編譯時期設定且絕對不會變更。 使用常數需提供有意義的名稱，而不是特殊值的數字常值 \(「魔術數字 (magic numbers)」\)。  
  
> [!NOTE]
>  在 C# 中，[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞不能以 C 和 C++ 一般使用的方式來定義常數。  
  
 若要定義整數型別的常數值 (`int`、`byte` 等等)，請使用列舉類型。 如需詳細資訊，請參閱 [enum](../../../csharp/language-reference/keywords/enum.md)。  
  
 若要定義非整數常數，其中一個方法是將它們分組在名為 `Constants` 的單一靜態類別中。 如下列範例所示，這需要常數的所有參考都以類別名稱開頭。  
  
## <a name="example"></a>範例  
 [!code-cs[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 使用類別名稱限定詞，可協助確保您和其他常數使用者了解它是無法修改的常數。  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)

