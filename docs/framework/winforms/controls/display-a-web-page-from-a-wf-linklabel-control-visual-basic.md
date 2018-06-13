---
title: 如何：從 Windows Form LinkLabel 控制項顯示 Web 網頁 (Visual Basic)
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- LinkLabel1_LinkClicked
helpviewer_keywords:
- examples [Windows Forms], LinkLabel control
- Web pages [Windows Forms], displaying
- linking [Windows Forms], to Web pages from forms
- Windows Forms, linking to Web pages
- LinkLabel control [Windows Forms], examples
ms.assetid: 477a7398-5971-4de3-b24c-f49f32bdb28a
ms.openlocfilehash: a9964c8d333ea87dd995ec9111acc1a8ac1e79b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524179"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="8e502-102">如何：從 Windows Form LinkLabel 控制項顯示 Web 網頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e502-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="8e502-103">這個範例會顯示在預設瀏覽器網頁當使用者按一下 Windows Form<xref:System.Windows.Forms.LinkLabel>控制項。</span><span class="sxs-lookup"><span data-stu-id="8e502-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e502-104">範例</span><span class="sxs-lookup"><span data-stu-id="8e502-104">Example</span></span>  
  
```vb  
Private Sub Form1_Load(ByVal sender As System.Object, ByVal e _  
As System.EventArgs) Handles MyBase.Load  
    LinkLabel1.Text = "Click here to get more info."  
    LinkLabel1.Links.Add(6, 4, "www.microsoft.com")  
End Sub  
Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, ByVal _  
e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) Handles _  
LinkLabel1.LinkClicked  
    System.Diagnostics.Process.Start(e.Link.LinkData.ToString())  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e502-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="8e502-105">Compiling the Code</span></span>  
 <span data-ttu-id="8e502-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="8e502-106">This example requires:</span></span>  
  
-   <span data-ttu-id="8e502-107">名為 Windows Form `Form1`。</span><span class="sxs-lookup"><span data-stu-id="8e502-107">A Windows Form named `Form1`.</span></span>  
  
-   <span data-ttu-id="8e502-108">名為 `LinkLabel1` 的 <xref:System.Windows.Forms.LinkLabel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="8e502-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
-   <span data-ttu-id="8e502-109">使用中的網際網路連線。</span><span class="sxs-lookup"><span data-stu-id="8e502-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8e502-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8e502-110">.NET Framework Security</span></span>  
 <span data-ttu-id="8e502-111">若要呼叫<xref:System.Diagnostics.Process.Start%2A>方法需要完全信任。</span><span class="sxs-lookup"><span data-stu-id="8e502-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="8e502-112">如需詳細資訊，請參閱<xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="8e502-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e502-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e502-113">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="8e502-114">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="8e502-114">LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
