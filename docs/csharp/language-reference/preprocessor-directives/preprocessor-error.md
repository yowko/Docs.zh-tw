---
title: '#error (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269395"
---
# <a name="error-c-reference"></a>#error (C# 參考)
`#error` 可讓您從程式碼中的特定位置產生錯誤。 例如:   
  
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
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
