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
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="949e4-102">HOW TO：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="949e4-102">How to: Inherit Windows Forms</span></span>

<span data-ttu-id="949e4-103">藉由繼承自基底表單建立新的 Windows Form，可以很快地複製您的最佳成果，而無須在每次需要它時都要完成重建表單的程序。</span><span class="sxs-lookup"><span data-stu-id="949e4-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>

<span data-ttu-id="949e4-104">如需在設計階段使用 [**繼承選取器**] 對話方塊繼承表單的詳細資訊, 以及如何以視覺化方式區分繼承控制項的[安全性層級, 請參閱如何:使用 [繼承選取器] 對話方塊](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)繼承表單。</span><span class="sxs-lookup"><span data-stu-id="949e4-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>

> [!NOTE]
> <span data-ttu-id="949e4-105">為了繼承自表單, 包含該表單的檔案或命名空間必須已內建至可執行檔或 DLL。</span><span class="sxs-lookup"><span data-stu-id="949e4-105">In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="949e4-106">若要建置專案，請從 [建置] 功能表中選擇 [建置]。</span><span class="sxs-lookup"><span data-stu-id="949e4-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="949e4-107">此外，命名空間的參考也必須加入至繼承表單的類別。</span><span class="sxs-lookup"><span data-stu-id="949e4-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span>

## <a name="inherit-a-form-programmatically"></a><span data-ttu-id="949e4-108">以程式設計方式繼承表單</span><span class="sxs-lookup"><span data-stu-id="949e4-108">Inherit a form programmatically</span></span>

1. <span data-ttu-id="949e4-109">在類別中，加入對包含您想要繼承之表單的命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="949e4-109">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>

2. <span data-ttu-id="949e4-110">在類別定義中，加入要繼承之表單的參考。</span><span class="sxs-lookup"><span data-stu-id="949e4-110">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="949e4-111">參考必須包括包含表單的命名空間，後面接著句點，然後是基底表單本身的名稱。</span><span class="sxs-lookup"><span data-stu-id="949e4-111">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 <span data-ttu-id="949e4-112">繼承表單時，請記住，呼叫兩次事件處理常式可能會發生問題，因為每個事件都會由基底類別和繼承的類別處理。</span><span class="sxs-lookup"><span data-stu-id="949e4-112">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="949e4-113">如需如何避免這個問題的詳細資訊，請參閱[針對 Visual Basic 中的繼承事件處理常式進行疑難排解](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="949e4-113">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="949e4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="949e4-114">See also</span></span>

- [<span data-ttu-id="949e4-115">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="949e4-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="949e4-116">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="949e4-116">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="949e4-117">using</span><span class="sxs-lookup"><span data-stu-id="949e4-117">using</span></span>](../../../csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="949e4-118">修改基底表單外觀的效果</span><span class="sxs-lookup"><span data-stu-id="949e4-118">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="949e4-119">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="949e4-119">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
