---
title: HOW TO：處理 Windows Forms 控制項中的使用者輸入事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: ae230f22c929be39ea00eafe378c6910c4a9d35f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592093"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="60596-102">HOW TO：處理 Windows Forms 控制項中的使用者輸入事件</span><span class="sxs-lookup"><span data-stu-id="60596-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="60596-103">此範例示範如何處理 Windows Form 控制項中可能發生的大部分鍵盤、滑鼠、焦點和驗證事件。</span><span class="sxs-lookup"><span data-stu-id="60596-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="60596-104">名為 `TextBoxInput` 的文字方塊中有焦點時，會接收那些事件，而每個事件的相關資訊，會依據事件引發的順序，寫入名為 `TextBoxOutput` 的文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="60596-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="60596-105">應用程式中也包含一組核取方塊，可用來篩選所要報告的事件。</span><span class="sxs-lookup"><span data-stu-id="60596-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60596-106">範例</span><span class="sxs-lookup"><span data-stu-id="60596-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60596-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="60596-107">Compiling the Code</span></span>  
 <span data-ttu-id="60596-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="60596-108">This example requires:</span></span>  
  
- <span data-ttu-id="60596-109">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="60596-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60596-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60596-110">See also</span></span>

- [<span data-ttu-id="60596-111">Windows Forms 中的使用者輸入</span><span class="sxs-lookup"><span data-stu-id="60596-111">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)
