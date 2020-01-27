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
# <a name="how-to-display-a-web-page-from-a-windows-forms-linklabel-control-visual-basic"></a>如何：從 Windows Form LinkLabel 控制項顯示 Web 網頁 (Visual Basic)
這個範例會在使用者按一下 Windows Forms <xref:System.Windows.Forms.LinkLabel> 控制項時，在預設瀏覽器中顯示網頁。  
  
## <a name="example"></a>範例  
  
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
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `Form1`的 Windows Form。  
  
- 名為 `LinkLabel1` 的 <xref:System.Windows.Forms.LinkLabel> 控制項。  
  
- 作用中的網際網路連接。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫 <xref:System.Diagnostics.Process.Start%2A> 方法需要完全信任。 如需詳細資訊，請參閱<xref:System.Security.SecurityException>。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.LinkLabel>
- [LinkLabel 控制項](linklabel-control-windows-forms.md)
