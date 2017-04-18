---
title: "如何：使用修飾詞和 GenerateMember 屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_GenerateMember"
  - "Designer_Modifiers"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "基底表單"
  - "表單繼承"
  - "GenerateMember 屬性"
  - "繼承, 表單"
  - "繼承的表單"
  - "繼承的表單, Windows Form"
  - "Modifiers 屬性"
  - "Windows Form, 繼承"
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：使用修飾詞和 GenerateMember 屬性
當您將元件置於 Windows Form 時，設計環境會提供兩個屬性：`GenerateMember` 和 `Modifiers`。  `GenerateMember` 屬性會指定 Windows Form 設計工具產生元件之成員變數的時機。  `Modifiers` 屬性是指派給該成員變數的存取修飾詞。  如果 `GenerateMember` 屬性的值是 `false`，`Modifiers` 屬性的值就沒有作用。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要指定元件是否為表單成員  
  
1.  在 Windows Form 設計工具中開啟表單。  
  
2.  開啟 \[**工具箱**\]，然後在表單上放置三個 <xref:System.Windows.Forms.Button> 控制項。  
  
3.  根據下表設定每個 <xref:System.Windows.Forms.Button> 控制項的 `GenerateMember` 和 `Modifiers` 屬性。  
  
    |按鈕名稱|GenerateMember 值|修飾詞值|  
    |----------|----------------------|----------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|沒有變更|  
  
4.  建置方案。  
  
5.  在 \[**方案總管**\] 中按一下 \[**顯示所有檔案**\] 按鈕。  
  
6.  開啟 \[**Form1**\] 節點，然後在 \[**程式碼編輯器**\] 中，開啟 \[**Form1.Designer.vb**\] 或 \[**Form1.Designer.cs**\] 檔。  這個檔案包含  Windows Form 設計工具所發出的程式碼。  
  
7.  尋找三個按鈕的宣告。  下列程式碼範例示範 `GenerateMember` 和 `Modifiers` 屬性指定的差異。  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  根據預設，Windows Form 設計工具會將 `private` \(Visual Basic 中的 `Friend`\) 修飾詞 \(Modifier\) 指派給像是 <xref:System.Windows.Forms.Panel> 的容器 \(Container\) 控制項。  如果您的基底 <xref:System.Windows.Forms.UserControl> 或 <xref:System.Windows.Forms.Form> 具有容器控制項，其將不會在繼承的控制項和表單中接受新的子系。  解決方案是將基底容器控制項的修飾詞，變更成 `protected` 或 `public`。  
  
## 請參閱  
 <xref:System.Windows.Forms.Button>   
 [Windows Form 視覺繼承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)   
 [逐步解說：示範視覺化繼承](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)   
 [如何：繼承 Windows Form](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)