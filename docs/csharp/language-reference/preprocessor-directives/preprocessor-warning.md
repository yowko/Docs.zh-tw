---
title: '#warning (C# 參考)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932673"
---
# <a name="warning-c-reference"></a>#warning (C# 參考)
`#warning` 可讓您從程式碼中的特定位置產生 [CS1030](../../misc/cs1030.md) 層級一的編譯器警告。 例如:   
  
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

## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)
