---
title: "如何：使用修飾詞和 GenerateMember 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcb79525e557a66ed471bc38dcbdd444d75ba6b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="58986-102">如何：使用修飾詞和 GenerateMember 屬性</span><span class="sxs-lookup"><span data-stu-id="58986-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="58986-103">當您將元件放在 Windows Form 上時，提供兩個屬性，以在設計環境：`GenerateMember`和`Modifiers`。</span><span class="sxs-lookup"><span data-stu-id="58986-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="58986-104">`GenerateMember`屬性會指定當 Windows Form 設計工具產生元件的成員變數。</span><span class="sxs-lookup"><span data-stu-id="58986-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="58986-105">`Modifiers`屬性是指派給該成員變數的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="58986-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="58986-106">如果值`GenerateMember`屬性是`false`，值`Modifiers`屬性沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="58986-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58986-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="58986-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="58986-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="58986-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="58986-109">如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。</span><span class="sxs-lookup"><span data-stu-id="58986-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="58986-110">若要指定元件是否為表單的成員</span><span class="sxs-lookup"><span data-stu-id="58986-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="58986-111">在 Windows Form 設計工具中，開啟您的表單。</span><span class="sxs-lookup"><span data-stu-id="58986-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="58986-112">開啟**工具箱**，並在表單中，將三個<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="58986-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="58986-113">設定`GenerateMember`和`Modifiers`每個屬性<xref:System.Windows.Forms.Button>根據下表的控制項。</span><span class="sxs-lookup"><span data-stu-id="58986-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="58986-114">按鈕名稱</span><span class="sxs-lookup"><span data-stu-id="58986-114">Button name</span></span>|<span data-ttu-id="58986-115">GenerateMember 值</span><span class="sxs-lookup"><span data-stu-id="58986-115">GenerateMember value</span></span>|<span data-ttu-id="58986-116">修飾詞值</span><span class="sxs-lookup"><span data-stu-id="58986-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="58986-117">沒有變更</span><span class="sxs-lookup"><span data-stu-id="58986-117">No change</span></span>|  
  
4.  <span data-ttu-id="58986-118">建置方案。</span><span class="sxs-lookup"><span data-stu-id="58986-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="58986-119">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="58986-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="58986-120">開啟**Form1**  節點，然後在**程式碼編輯器**，開啟**Form1.Designer.vb**或**Form1.Designer.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="58986-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="58986-121">此檔案包含 Windows Form 設計工具所發出的程式碼。</span><span class="sxs-lookup"><span data-stu-id="58986-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="58986-122">尋找三個按鈕的宣告。</span><span class="sxs-lookup"><span data-stu-id="58986-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="58986-123">下列程式碼範例顯示所指定的差異`GenerateMember`和`Modifiers`屬性。</span><span class="sxs-lookup"><span data-stu-id="58986-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="58986-124">根據預設，Windows Form 設計工具會指派`private`(`Friend`在 Visual Basic 中) 類似容器控制項的修飾詞<xref:System.Windows.Forms.Panel>。</span><span class="sxs-lookup"><span data-stu-id="58986-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="58986-125">如果您的基底<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Form>有容器的控制項，就不會接受繼承的控制項和表單中的新子系。</span><span class="sxs-lookup"><span data-stu-id="58986-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="58986-126">解決方法是將基底容器控制項的修飾詞變更`protected`或`public`。</span><span class="sxs-lookup"><span data-stu-id="58986-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58986-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58986-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="58986-128">Windows Forms 視覺繼承</span><span class="sxs-lookup"><span data-stu-id="58986-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="58986-129">逐步解說：示範視覺化繼承</span><span class="sxs-lookup"><span data-stu-id="58986-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="58986-130">如何：繼承 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="58986-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
