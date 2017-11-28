---
title: "如何：在 C# 中定義常數"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ff12d0b6882289da9ed924f1c7de00edc5dc1e2e
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-define-constants-in-c"></a>如何：在 C# 中定義常數
常數是欄位，其值於編譯時期設定且絕對不會變更。 使用常數提供有意義的名稱，而不是特殊值的數值常值 (「神奇號碼」)。  
  
> [!NOTE]
>  在 C# 中，[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞不能以 C 和 C++ 一般使用的方式來定義常數。  
  
 若要定義整數型別的常數值 (`int`、`byte` 等等)，請使用列舉類型。 如需詳細資訊，請參閱 [enum](../../../csharp/language-reference/keywords/enum.md)。  
  
 若要定義非整數常數，其中一個方法是將它們分組在名為 `Constants` 的單一靜態類別中。 如下列範例所示，這需要常數的所有參考都以類別名稱開頭。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 使用類別名稱限定詞，可協助確保您和其他常數使用者了解它是無法修改的常數。  
  
## <a name="see-also"></a>另請參閱  
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)
