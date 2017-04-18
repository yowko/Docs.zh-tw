---
title: "為 Windows Form 上的控制項提供可及性資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Forms 控制項, 協助工具"
  - "控制項 [Windows Forms], 協助工具"
  - "協助工具, Windows Forms 控制項"
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 為 Windows Form 上的控制項提供可及性資訊
協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。 範例包括針對視障人士的螢幕助讀程式，以及提供口頭指令，而不是使用滑鼠或鍵盤的人所適用的語音輸入公用程式。 這些協助工具會與 Windows Forms 控制項所公開的協助工具屬性互動。 這些屬性是：  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## AccessibilityObject 屬性  
 這個唯讀屬性包含 [AccessibleObject 類別](frlrfSystemWindowsFormsAccessibleObjectClassTopic)執行個體。**AccessibleObject** 實作 <xref:Accessibility.IAccessible> 介面，它提供控制項的描述、螢幕位置、瀏覽功能和值等相關資訊。 當控制項加入表單中時，設計工具會設定此值。  
  
## AccessibleDefaultActionDescription 屬性  
 這個字串描述控制項的動作。 它不會出現在 \[屬性\] 視窗中，並且只能在程式碼中設定。 下列範例會為按鈕控制項設定此屬性：  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## AccessibleDescription 屬性  
 這個字串描述控制項。 它可能在 \[屬性\] 視窗或在程式碼中設定，如下所示：  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## AccessibleName 屬性  
 這是報告給協助工具輔助的控制項名稱。 它可能在 \[屬性\] 視窗或在程式碼中設定，如下所示：  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## AccessibleRole 屬性  
 此屬性，其中包含 [AccessibleRole Enumeration](frlrfSystemWindowsFormsAccessibleRoleClassTopic) 列舉，描述控制項的使用者介面角色。 新控制項的值會設定為 `Default`。 這表示，根據預設，**Button** 控制項可當做 **Button**。 如果控制項具有另一個角色，您可能會想重設這個屬性。 例如，您可能使用 **PictureBox** 控制項作為 **Chart**，而您想要協助工具輔助將角色報告為 **Chart**，不是 **PictureBox**。 您也可能想要為您開發的自訂控制項指定這個屬性。 這個屬性可能在 \[屬性\] 視窗或在程式碼中設定，如下所示：  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## 請參閱  
 <xref:System.Windows.Forms.AccessibleObject>   
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.AccessibleRole>