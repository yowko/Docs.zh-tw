---
title: 如何在 C# 中定義常數
description: '瞭解如何在 c # 中定義常數，也就是值在編譯時期設定的欄位。 使用常數為特殊值提供有意義的名稱。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 4ee1b04cf30b7602ae563cb02daed49f82c04de7
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898992"
---
# <a name="how-to-define-constants-in-c"></a>如何在 C 中定義常數\#

常數是欄位，其值於編譯時期設定且絕對不會變更。 使用常數提供有意義的名稱，而不是特殊值的數值常值 (「神奇號碼」)。  
  
> [!NOTE]
> 在 C# 中，[#define](../../language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞不能以 C 和 C++ 一般使用的方式來定義常數。  
  
 若要定義整數型別的常數值 (`int`、`byte` 等等)，請使用列舉類型。 如需詳細資訊，請參閱 [enum](../../language-reference/builtin-types/enum.md)。  
  
 若要定義非整數常數，其中一個方法是將它們分組在名為 `Constants` 的單一靜態類別中。 如下列範例所示，這需要常數的所有參考都以類別名稱開頭。  
  
## <a name="example"></a>範例  

 [!code-csharp[constants](snippets/how-to-define-constants/Program.cs)]  
  
 使用類別名稱限定詞，可協助確保您和其他常數使用者了解它是無法修改的常數。  
  
## <a name="see-also"></a>另請參閱

- [類別和結構](./index.md)
