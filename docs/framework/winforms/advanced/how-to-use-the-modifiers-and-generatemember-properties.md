---
title: HOW TO：使用修飾詞和 GenerateMember 屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 3fbaaae53aa60f6356c3a8daa0513de86ef2dacb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211285"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="6b82f-102">HOW TO：使用修飾詞和 GenerateMember 屬性</span><span class="sxs-lookup"><span data-stu-id="6b82f-102">How to: Use the Modifiers and GenerateMember Properties</span></span>

<span data-ttu-id="6b82f-103">當您將元件放在 Windows Form 上時，在設計環境所提供兩個屬性：`GenerateMember`和`Modifiers`。</span><span class="sxs-lookup"><span data-stu-id="6b82f-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="6b82f-104">`GenerateMember`屬性會指定當 Windows Form 設計工具產生元件的成員變數。</span><span class="sxs-lookup"><span data-stu-id="6b82f-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="6b82f-105">`Modifiers`屬性是指派給該成員變數的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="6b82f-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="6b82f-106">如果值`GenerateMember`屬性是`false`，值`Modifiers`屬性沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="6b82f-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>

## <a name="specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="6b82f-107">指定元件是否為表單的成員</span><span class="sxs-lookup"><span data-stu-id="6b82f-107">Specify whether a component is a member of the form</span></span>

1. <span data-ttu-id="6b82f-108">在 Visual Studio 中，在 Windows Form 設計工具中，開啟您的表單。</span><span class="sxs-lookup"><span data-stu-id="6b82f-108">In Visual Studio, in the Windows Forms Designer, open your form.</span></span>

2. <span data-ttu-id="6b82f-109">開啟**工具箱**，並在表單中，將三個<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="6b82f-109">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>

3. <span data-ttu-id="6b82f-110">設定`GenerateMember`並`Modifiers`每個屬性<xref:System.Windows.Forms.Button>根據下表的控制項。</span><span class="sxs-lookup"><span data-stu-id="6b82f-110">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>

    |<span data-ttu-id="6b82f-111">按鈕名稱</span><span class="sxs-lookup"><span data-stu-id="6b82f-111">Button name</span></span>|<span data-ttu-id="6b82f-112">GenerateMember 值</span><span class="sxs-lookup"><span data-stu-id="6b82f-112">GenerateMember value</span></span>|<span data-ttu-id="6b82f-113">修飾詞值</span><span class="sxs-lookup"><span data-stu-id="6b82f-113">Modifiers value</span></span>|
    |-----------------|--------------------------|---------------------|
    |`button1`|`true`|`private`|
    |`button2`|`true`|`protected`|
    |`button3`|`false`|<span data-ttu-id="6b82f-114">沒有變更</span><span class="sxs-lookup"><span data-stu-id="6b82f-114">No change</span></span>|

4. <span data-ttu-id="6b82f-115">建置方案。</span><span class="sxs-lookup"><span data-stu-id="6b82f-115">Build the solution.</span></span>

5. <span data-ttu-id="6b82f-116">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6b82f-116">In **Solution Explorer**, click the **Show All Files** button.</span></span>

6. <span data-ttu-id="6b82f-117">開啟**Form1**節點，然後在**程式碼編輯器**，開啟**Form1.Designer.vb**或是**Form1.Designer.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="6b82f-117">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="6b82f-118">此檔案包含 Windows Form 設計工具所發出的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6b82f-118">This file contains the code emitted by the Windows Forms Designer.</span></span>

7. <span data-ttu-id="6b82f-119">尋找三個按鈕的宣告。</span><span class="sxs-lookup"><span data-stu-id="6b82f-119">Find the declarations for the three buttons.</span></span> <span data-ttu-id="6b82f-120">下列程式碼範例顯示所指定的差異`GenerateMember`和`Modifiers`屬性。</span><span class="sxs-lookup"><span data-stu-id="6b82f-120">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>

     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]

     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]

> [!NOTE]
> <span data-ttu-id="6b82f-121">根據預設，Windows Form 設計工具會指派`private`(`Friend` Visual Basic 中) 等容器控制項的修飾詞<xref:System.Windows.Forms.Panel>。</span><span class="sxs-lookup"><span data-stu-id="6b82f-121">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="6b82f-122">如果您的基底<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Form>有容器控制項，它將不會接受新的子系繼承的控制項和表單中。</span><span class="sxs-lookup"><span data-stu-id="6b82f-122">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="6b82f-123">解決方法是變更的基底容器控制項的修飾詞`protected`或`public`。</span><span class="sxs-lookup"><span data-stu-id="6b82f-123">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6b82f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b82f-124">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="6b82f-125">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="6b82f-125">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
- [<span data-ttu-id="6b82f-126">逐步解說：示範視覺化繼承</span><span class="sxs-lookup"><span data-stu-id="6b82f-126">Walkthrough: Demonstrating Visual Inheritance</span></span>](walkthrough-demonstrating-visual-inheritance.md)
- [<span data-ttu-id="6b82f-127">如何：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b82f-127">How to: Inherit Windows Forms</span></span>](how-to-inherit-windows-forms.md)
