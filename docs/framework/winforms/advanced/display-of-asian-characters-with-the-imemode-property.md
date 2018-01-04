---
title: "使用 ImeMode 屬性顯示亞洲字元"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="7384e-102">使用 ImeMode 屬性顯示亞洲字元</span><span class="sxs-lookup"><span data-stu-id="7384e-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="7384e-103"><xref:System.Windows.Forms.Control.ImeMode%2A>屬性可由表單和控制項來強制特定模式的輸入的法 (ime)。</span><span class="sxs-lookup"><span data-stu-id="7384e-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="7384e-104">IME 是撰寫中文、日文和韓文字的重要元件，因為這些書寫系統的字元數比可以為一般鍵盤編碼的字元數還要多。</span><span class="sxs-lookup"><span data-stu-id="7384e-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="7384e-105">例如，您可能只要在特定文字方塊中允許 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="7384e-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="7384e-106">您可以在此情況下設定<xref:System.Windows.Forms.Control.ImeMode%2A>屬性<xref:System.Windows.Forms.ImeMode>使用者僅能為該特定的文字方塊中輸入 ASCII 字元。</span><span class="sxs-lookup"><span data-stu-id="7384e-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="7384e-107">預設值<xref:System.Windows.Forms.Control.ImeMode%2A>屬性是<xref:System.Windows.Forms.ImeMode>，因此如果您設定表單的屬性，在表單上的所有控制項將會都繼承該設定。</span><span class="sxs-lookup"><span data-stu-id="7384e-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="7384e-108">如需詳細資訊，請參閱<xref:System.Windows.Forms.Control.ImeMode%2A>) 和<xref:System.Windows.Forms.ImeMode>。</span><span class="sxs-lookup"><span data-stu-id="7384e-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7384e-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="7384e-109">See Also</span></span>  
 [<span data-ttu-id="7384e-110">全球化 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7384e-110">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
