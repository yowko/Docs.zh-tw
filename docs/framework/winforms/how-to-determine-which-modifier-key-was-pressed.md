---
title: HOW TO：判斷哪一個輔助按鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 58fdea3df3d82aa9f36244a11c6d353019c7ac49
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665013"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="113da-102">HOW TO：判斷哪一個輔助按鍵</span><span class="sxs-lookup"><span data-stu-id="113da-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="113da-103">當您建立可接受使用者的按鍵輸入時，您也可以監視輔助按鍵，例如 SHIFT、 ALT 和 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="113da-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="113da-104">輔助按鍵按下時搭配其他索引鍵，或按下滑鼠，就可以適當地回應您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="113da-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="113da-105">例如，如果按下以字母 S 時，這只會出現在畫面上，"s"，但如果按下按鍵 CTRL + S，可能會儲存目前的文件。</span><span class="sxs-lookup"><span data-stu-id="113da-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="113da-106">如果您處理<xref:System.Windows.Forms.Control.KeyDown>事件，<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>屬性<xref:System.Windows.Forms.KeyEventArgs>收到事件處理常式會指定哪一個輔助按鍵按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="113da-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="113da-107">或者，<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>屬性<xref:System.Windows.Forms.KeyEventArgs>指定按鍵以及與位元 OR 運算結合任何輔助按鍵的字元。</span><span class="sxs-lookup"><span data-stu-id="113da-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="113da-108">不過，如果您處理<xref:System.Windows.Forms.Control.KeyPress>事件或滑鼠事件，事件處理常式不會收到這項資訊。</span><span class="sxs-lookup"><span data-stu-id="113da-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="113da-109">在此情況下，您必須使用<xref:System.Windows.Forms.Control.ModifierKeys%2A>屬性<xref:System.Windows.Forms.Control>類別。</span><span class="sxs-lookup"><span data-stu-id="113da-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="113da-110">在任一情況下，您必須執行適當的位元 AND<xref:System.Windows.Forms.Keys>值和您要測試的值。</span><span class="sxs-lookup"><span data-stu-id="113da-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="113da-111"><xref:System.Windows.Forms.Keys>列舉型別提供具有正確的值和每個修飾詞索引鍵，因此是很重要，您執行位元的變化。</span><span class="sxs-lookup"><span data-stu-id="113da-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="113da-112">比方說，SHIFT 鍵表示<xref:System.Windows.Forms.Keys.Shift>， <xref:System.Windows.Forms.Keys.ShiftKey>，<xref:System.Windows.Forms.Keys.RShiftKey>並<xref:System.Windows.Forms.Keys.LShiftKey>正確的值來測試 SHIFT 輔助按鍵是<xref:System.Windows.Forms.Keys.Shift>。</span><span class="sxs-lookup"><span data-stu-id="113da-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="113da-113">同樣地，若要測試 CTRL 和 ALT 修飾詞為您應該使用<xref:System.Windows.Forms.Keys.Control>和<xref:System.Windows.Forms.Keys.Alt>值，分別。</span><span class="sxs-lookup"><span data-stu-id="113da-113">Similarly, to test for CTRL and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="113da-114">Visual Basic 程式設計人員也可以存取金鑰的資訊透過<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>屬性</span><span class="sxs-lookup"><span data-stu-id="113da-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="113da-115">若要判斷哪一個輔助按鍵</span><span class="sxs-lookup"><span data-stu-id="113da-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="113da-116">使用位元`AND`運算子搭配<xref:System.Windows.Forms.Control.ModifierKeys%2A>屬性和值的<xref:System.Windows.Forms.Keys>列舉型別來判斷特定的修飾詞的索引鍵是否按下。</span><span class="sxs-lookup"><span data-stu-id="113da-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="113da-117">下列程式碼範例示範如何判斷是否在按下 SHIFT 鍵<xref:System.Windows.Forms.Control.KeyPress>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="113da-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="113da-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="113da-118">See also</span></span>
- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [<span data-ttu-id="113da-119">Windows Forms 應用程式中的鍵盤輸入</span><span class="sxs-lookup"><span data-stu-id="113da-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
- <span data-ttu-id="113da-120">[如何：決定如果 CapsLock 是在 Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="113da-120">[How to: Determine If CapsLock is On in Visual Basic](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))</span></span>
