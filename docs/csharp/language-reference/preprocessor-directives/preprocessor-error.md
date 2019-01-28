---
title: '#error - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559331"
---
# <a name="error-c-reference"></a>#error (C# 參考)
`#error` 可讓您從您程式碼中的特定位置產生 [CS1029](../compiler-messages/cs1029.md) 使用者定義錯誤。 例如：  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>備註  
 `#error` 常見於條件指示詞中。  
  
 也可以使用 [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) 產生使用者定義警告。  
  
## <a name="example"></a>範例  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
