---
title: 從 LinkLabel 控制項顯示網頁（Visual Basic）
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
ms.openlocfilehash: 75373d55b7bc5ef11e39d5b9546996cb1c4f6f7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745923"
---
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a><span data-ttu-id="b9b7d-102">如何：從 Windows Form LinkLabel 控制項顯示 Web 網頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9b7d-102">How to: Display a Web Page from a Windows Forms LinkLabel Control (Visual Basic)</span></span>
<span data-ttu-id="b9b7d-103">這個範例會在使用者按一下 Windows Forms <xref:System.Windows.Forms.LinkLabel> 控制項時，在預設瀏覽器中顯示網頁。</span><span class="sxs-lookup"><span data-stu-id="b9b7d-103">This example displays a Web page in the default browser when a user clicks a Windows Forms <xref:System.Windows.Forms.LinkLabel> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9b7d-104">範例</span><span class="sxs-lookup"><span data-stu-id="b9b7d-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9b7d-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b9b7d-105">Compiling the Code</span></span>  
 <span data-ttu-id="b9b7d-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b9b7d-106">This example requires:</span></span>  
  
- <span data-ttu-id="b9b7d-107">名為 `Form1`的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="b9b7d-107">A Windows Form named `Form1`.</span></span>  
  
- <span data-ttu-id="b9b7d-108">名為 `LinkLabel1` 的 <xref:System.Windows.Forms.LinkLabel> 控制項。</span><span class="sxs-lookup"><span data-stu-id="b9b7d-108">A <xref:System.Windows.Forms.LinkLabel> control named `LinkLabel1`.</span></span>  
  
- <span data-ttu-id="b9b7d-109">作用中的網際網路連接。</span><span class="sxs-lookup"><span data-stu-id="b9b7d-109">An active Internet connection.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b9b7d-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b9b7d-110">.NET Framework Security</span></span>  
 <span data-ttu-id="b9b7d-111">呼叫 <xref:System.Diagnostics.Process.Start%2A> 方法需要完全信任。</span><span class="sxs-lookup"><span data-stu-id="b9b7d-111">The call to the <xref:System.Diagnostics.Process.Start%2A> method requires full trust.</span></span> <span data-ttu-id="b9b7d-112">如需詳細資訊，請參閱<xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="b9b7d-112">For more information, see <xref:System.Security.SecurityException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b7d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b7d-113">See also</span></span>

- <xref:System.Windows.Forms.LinkLabel>
- [<span data-ttu-id="b9b7d-114">LinkLabel 控制項</span><span class="sxs-lookup"><span data-stu-id="b9b7d-114">LinkLabel Control</span></span>](linklabel-control-windows-forms.md)
