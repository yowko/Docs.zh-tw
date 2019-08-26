---
title: '##pragma warning - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma warning'
helpviewer_keywords:
- '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
ms.openlocfilehash: dc221235e78a187f921815ed6e6c7750778014d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922268"
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (C# 參考)
`#pragma warning` 可以啟用或停用特定警告。  
  
## <a name="syntax"></a>語法  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
## <a name="parameters"></a>參數  
 `warning-list`  
 警告編號的逗點分隔清單。 "CS" 前置詞是選擇性的。  
  
 未指定警告編號時，`disable` 會停用所有警告，而 `restore` 會啟用所有警告。  
  
> [!NOTE]
> 若要尋找 Visual Studio 中的警告編號，請建立專案，然後在 [輸出]  視窗中尋找警告編號。  
  
## <a name="example"></a>範例  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 前置處理器指示詞](./index.md)
- [C# 編譯器錯誤](../compiler-messages/index.md)
