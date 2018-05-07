---
title: 支援可及性方針的 Windows Form 控制項屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b466dcf42561d8ced7b224215538a807c94b174b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>支援可及性方針的 Windows Form 控制項屬性
控制項 Windows Form 的標準工具箱支援許多協助工具的指導方針，包括鍵盤焦點，而且已公開螢幕項目。  
  
## <a name="planning-ahead-for-accessibility"></a>事先規劃協助工具  
 控制項的屬性可以用來支援其他協助工具的指導方針下, 表所示。 此外，您應該使用功能表來提供存取權的程式功能。  
  
|控制項屬性|協助工具的考量|  
|----------------------|--------------------------------------|  
|AccessibleDescription|描述被報告給協助工具，例如螢幕助讀程式。 協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。|  
|AccessibleName|將報告給協助工具的名稱。|  
|AccessibleRole|描述使用在使用者介面項目。|  
|TabIndex|建立表單直覺式導覽路徑。 請務必沒有內建函式標記，例如文字方塊中，將其關聯的標籤它們定位順序中之前的控制項。|  
|Text|您可以使用"&"字元來建立便捷鍵。 使用存取金鑰是提供記載的鍵盤存取功能的一部分。|  
|字型大小|如果字型不是可調整的則它應該設為 10 或更大。 一旦設定表單的字型大小，之後加入至表單的所有控制項將會都有相同的大小。|  
|Forecolor|如果這個屬性設定為預設值，然後將會在表單上使用使用者的色彩設定。|  
|Backcolor|如果這個屬性設定為預設值，然後將會在表單上使用使用者的色彩設定。|  
|BackgroundImage|將此屬性保留空白，讓文字更容易閱讀。|  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：建立 Windows 架構的協助工具應用程式](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
