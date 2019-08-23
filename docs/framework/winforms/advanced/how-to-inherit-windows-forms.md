---
title: 作法：繼承 Windows Forms
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: a6d000bc853046cffbc2bddc54d1f5faec689032
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968606"
---
# <a name="how-to-inherit-windows-forms"></a>HOW TO：繼承 Windows Forms

藉由繼承自基底表單建立新的 Windows Form，可以很快地複製您的最佳成果，而無須在每次需要它時都要完成重建表單的程序。

如需在設計階段使用 [**繼承選取器**] 對話方塊繼承表單的詳細資訊, 以及如何以視覺化方式區分繼承控制項的[安全性層級, 請參閱如何:使用 [繼承選取器] 對話方塊](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)繼承表單。

> [!NOTE]
> 為了繼承自表單, 包含該表單的檔案或命名空間必須已內建至可執行檔或 DLL。 若要建置專案，請從 [建置] 功能表中選擇 [建置]。 此外，命名空間的參考也必須加入至繼承表單的類別。

## <a name="inherit-a-form-programmatically"></a>以程式設計方式繼承表單

1. 在類別中，加入對包含您想要繼承之表單的命名空間的參考。

2. 在類別定義中，加入要繼承之表單的參考。 參考必須包括包含表單的命名空間，後面接著句點，然後是基底表單本身的名稱。

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 繼承表單時，請記住，呼叫兩次事件處理常式可能會發生問題，因為每個事件都會由基底類別和繼承的類別處理。 如需如何避免這個問題的詳細資訊，請參閱[針對 Visual Basic 中的繼承事件處理常式進行疑難排解](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。

## <a name="see-also"></a>另請參閱

- [Inherits 陳述式](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](../../../csharp/language-reference/keywords/using.md)
- [修改基底表單外觀的效果](effects-of-modifying-base-form-appearance.md)
- [Windows Forms 視覺繼承](windows-forms-visual-inheritance.md)
