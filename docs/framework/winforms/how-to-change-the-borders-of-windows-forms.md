---
title: "如何：變更 Windows Form 的框線 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Form, 變更框線"
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：變更 Windows Form 的框線
在決定 Windows Form 的外觀和行為時，您有幾種框線樣式可以選擇。  藉由變更 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性，您可以控制表單的調整大小行為。  此外，設定 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 也會影響標題列的顯示方式，以及所出現在標題列上的按鈕。  如需詳細資訊，請參閱<xref:System.Windows.Forms.FormBorderStyle>。  
  
 在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中對這項工作有廣泛的支援。  
  
 請參閱[如何：使用設計工具變更 Windows Form 的框線](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\))。  
  
### 以程式設計方式設定 Windows Form 的框線樣式  
  
-   將 <xref:System.Windows.Forms.Form.FormBorderStyle%2A> 屬性設定為您想要的樣式。  下列程式碼範例將表單 `DlgBx1`  的框線樣式設定為 <xref:System.Windows.Forms.FormBorderStyle>。  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     另請參閱[如何：在設計階段建立對話方塊](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))。  
  
     此外，如果您為提供選擇性 \[最小化\] 和 \[最大化\] 按鈕的表單選擇框線樣式，可以指定是否要啟用其中一個或兩個按鈕的功能。  當您想要密切控制使用者經驗時，這些按鈕會很有用。  預設會啟用 \[最小化\] 和 \[最大化\] 按鈕，而按鈕的功能則是透過 \[屬性\] 視窗管理。  
  
## 請參閱  
 <xref:System.Windows.Forms.FormBorderStyle>   
 <xref:System.Windows.Forms.FormBorderStyle>   
 [Windows Form 使用者入門](../../../docs/framework/winforms/getting-started-with-windows-forms.md)