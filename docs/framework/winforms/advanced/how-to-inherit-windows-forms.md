---
title: 如何：繼承 Windows Form
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 275ae52a36ed9766e2569bd6c8ecdea78ea56e0b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868662"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="fcded-102">如何：繼承 Windows Form</span><span class="sxs-lookup"><span data-stu-id="fcded-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="fcded-103">藉由繼承自基底表單建立新的 Windows Form，可以很快地複製您的最佳成果，而無須在每次需要它時都要完成重建表單的程序。</span><span class="sxs-lookup"><span data-stu-id="fcded-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="fcded-104">如需在設計階段使用 [繼承選取器] 對話方塊繼承表單的詳細資訊，以及如何以視覺化方式區分繼承控制項的安全性層級，請參閱[如何：使用繼承選取器對話方塊繼承表單](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)。</span><span class="sxs-lookup"><span data-stu-id="fcded-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="fcded-105">**附註：** 為了繼承自表單，包含該表單的檔案或命名空間必須已建置為可執行檔或 DLL。</span><span class="sxs-lookup"><span data-stu-id="fcded-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="fcded-106">若要建置專案，請從 [建置] 功能表中選擇 [建置]。</span><span class="sxs-lookup"><span data-stu-id="fcded-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="fcded-107">此外，命名空間的參考也必須加入至繼承表單的類別。</span><span class="sxs-lookup"><span data-stu-id="fcded-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="fcded-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="fcded-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fcded-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="fcded-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fcded-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="fcded-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="fcded-111">以程式設計方式繼承表單</span><span class="sxs-lookup"><span data-stu-id="fcded-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="fcded-112">在類別中，加入對包含您想要繼承之表單的命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="fcded-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="fcded-113">在類別定義中，加入要繼承之表單的參考。</span><span class="sxs-lookup"><span data-stu-id="fcded-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="fcded-114">參考必須包括包含表單的命名空間，後面接著句點，然後是基底表單本身的名稱。</span><span class="sxs-lookup"><span data-stu-id="fcded-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="fcded-115">繼承表單時，請記住，呼叫兩次事件處理常式可能會發生問題，因為每個事件都會由基底類別和繼承的類別處理。</span><span class="sxs-lookup"><span data-stu-id="fcded-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="fcded-116">如需如何避免這個問題的詳細資訊，請參閱[針對 Visual Basic 中的繼承事件處理常式進行疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="fcded-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcded-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcded-117">See Also</span></span>  
 [<span data-ttu-id="fcded-118">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="fcded-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="fcded-119">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="fcded-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="fcded-120">using</span><span class="sxs-lookup"><span data-stu-id="fcded-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="fcded-121">修改基底表單外觀的效果</span><span class="sxs-lookup"><span data-stu-id="fcded-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="fcded-122">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="fcded-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
