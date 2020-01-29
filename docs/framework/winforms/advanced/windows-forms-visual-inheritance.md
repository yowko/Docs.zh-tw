---
title: 視覺繼承
ms.date: 03/30/2017
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inheritance
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 857eb737-3602-4d49-bd8b-f70d33ace345
ms.openlocfilehash: c6aa104a1c9ebe6f59c11ce70e3352169132e714
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732487"
---
# <a name="windows-forms-visual-inheritance"></a><span data-ttu-id="21720-102">Windows Form 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="21720-102">Windows Forms Visual Inheritance</span></span>
<span data-ttu-id="21720-103">有時候，您可能會決定讓專案呼叫類似您在前一個專案中建立的表單。</span><span class="sxs-lookup"><span data-stu-id="21720-103">Occasionally, you may decide that a project calls for a form similar to one that you have created in a previous project.</span></span> <span data-ttu-id="21720-104">或者，您可能想要建立基本表單，具有例如浮水印或特定控制項版面配置的設定，您稍後會在專案中再次使用，具有包含對原始表單範本修改的每個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="21720-104">Or, you may want to create a basic form with settings such as a watermark or certain control layout that you will then use again within a project, with each iteration containing modifications to the original form template.</span></span> <span data-ttu-id="21720-105">表單繼承可讓您建立基底表單，然後從它繼承並進行修改，同時保留您需要的任何原始設定。</span><span class="sxs-lookup"><span data-stu-id="21720-105">Form inheritance enables you to create a base form and then inherit from it and make modifications while preserving whatever original settings you need.</span></span>  
  
 <span data-ttu-id="21720-106">您可以程式設計方式或使用視覺繼承選取器，建立衍生類別表單。</span><span class="sxs-lookup"><span data-stu-id="21720-106">You can create derived-class forms programmatically or by using the Visual Inheritance picker.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21720-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="21720-107">In This Section</span></span>  
 [<span data-ttu-id="21720-108">如何：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21720-108">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)  
 <span data-ttu-id="21720-109">說明如何使用程式碼建立繼承的表單。</span><span class="sxs-lookup"><span data-stu-id="21720-109">Gives directions for creating inherited forms in code.</span></span>  
  
 [<span data-ttu-id="21720-110">如何：使用繼承選取器對話方塊繼承表單</span><span class="sxs-lookup"><span data-stu-id="21720-110">How to: Inherit Forms Using the Inheritance Picker Dialog Box</span></span>](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)  
 <span data-ttu-id="21720-111">說明如何使用繼承選取器建立繼承的表單。</span><span class="sxs-lookup"><span data-stu-id="21720-111">Gives directions for creating inherited forms with the Inheritance Picker.</span></span>  
  
 [<span data-ttu-id="21720-112">修改基底表單外觀的效果</span><span class="sxs-lookup"><span data-stu-id="21720-112">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)  
 <span data-ttu-id="21720-113">說明如何變更基底表單的控制項及其屬性。</span><span class="sxs-lookup"><span data-stu-id="21720-113">Gives directions for changing a base form's controls and their properties.</span></span>  
  
 [<span data-ttu-id="21720-114">逐步解說：示範視覺化繼承</span><span class="sxs-lookup"><span data-stu-id="21720-114">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)  
 <span data-ttu-id="21720-115">描述如何建立基底 Windows Form，並且將其編譯至類別庫。</span><span class="sxs-lookup"><span data-stu-id="21720-115">Describes how to create a base Windows Form and compile it into a class library.</span></span> <span data-ttu-id="21720-116">您將匯入此類別庫至另一個專案，並建立繼承自基底表單的新表單。</span><span class="sxs-lookup"><span data-stu-id="21720-116">You will import this class library into another project, and create a new form that inherits from the base form.</span></span>  
  
 [<span data-ttu-id="21720-117">如何：使用修飾詞和 GenerateMember 屬性</span><span class="sxs-lookup"><span data-stu-id="21720-117">How to: Use the Modifiers and GenerateMember Properties</span></span>](how-to-use-the-modifiers-and-generatemember-properties.md)  
 <span data-ttu-id="21720-118">說明如何使用 `GenerateMember` 和 `Modifiers` 屬性，當 Windows Form 設計工具產生元件的成員變數時，它們是相關的。</span><span class="sxs-lookup"><span data-stu-id="21720-118">Gives directions for using the `GenerateMember` and `Modifiers` properties, which are relevant when the Windows Forms Designer generates a member variable for a component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="21720-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="21720-119">Related Sections</span></span>  
 [<span data-ttu-id="21720-120">繼承基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21720-120">Inheritance basics (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 <span data-ttu-id="21720-121">描述如何定義做為其他類別基礎的 Visual Basic 類別。</span><span class="sxs-lookup"><span data-stu-id="21720-121">Describes how to define Visual Basic classes that serve as the basis for other classes.</span></span>  
  
 [<span data-ttu-id="21720-122">Class - 類別</span><span class="sxs-lookup"><span data-stu-id="21720-122">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 <span data-ttu-id="21720-123">描述類別的 C# 方法，其中允許單一繼承。</span><span class="sxs-lookup"><span data-stu-id="21720-123">Describes the C# approach of classes, in which single inheritance is allowed.</span></span>  
  
 [<span data-ttu-id="21720-124">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="21720-124">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="21720-125">列出繼承元件中事件處理常式所引發的常見問題</span><span class="sxs-lookup"><span data-stu-id="21720-125">Lists common issues that arise with event handlers in inherited components</span></span>
