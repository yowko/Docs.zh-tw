---
title: '#warning (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a>#warning (C# 參考)
`#warning` 可讓您從程式碼中的特定位置產生層級一的警告。 例如:   
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>備註  
 `#warning` 常見於條件指示詞中。 也可以使用 [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md) 產生使用者定義錯誤。  
  
## <a name="example"></a>範例  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
