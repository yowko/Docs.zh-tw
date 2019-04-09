---
title: 支援可及性方針的 Windows Form 控制項屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: b3f10fe472e449d39385facdbc716cba9b3f7382
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183777"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>支援可及性方針的 Windows Form 控制項屬性
標準 Windows forms 工具箱控制項都支援許多協助工具指導方針，包括鍵盤焦點的顯示，而且已公開螢幕項目。  
  
## <a name="planning-ahead-for-accessibility"></a>事先計劃，協助工具  
 控制項的屬性可用來支援其他協助工具方針下, 表所示。 此外，您應該使用功能表來提供存取權的程式功能。  
  
|控制項屬性|協助工具的考量|  
|----------------------|--------------------------------------|  
|AccessibleDescription|描述會回報給螢幕助讀程式之類的協助工具輔助。 協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。|  
|AccessibleName|將報告給協助工具輔助名稱。|  
|AccessibleRole|說明如何使用使用者介面中的項目。|  
|TabIndex|建立直覺式的巡覽路徑，透過表單。 請務必沒有內建的標記，例如文字方塊中，有其相關聯的標籤，緊接在其之前的定位順序中的控制項。|  
|文字|您可以使用"&"字元來建立存取金鑰。 使用存取金鑰是提供記載的鍵盤存取功能的一部分。|  
|字型大小|如果字型大小不是可調整的則它應該設為 10 或更大。 一旦設定表單的字型大小，之後加入至表單的所有控制項都會都有相同的大小。|  
|Forecolor|如果這個屬性設定為預設值，然後將使用使用者的色彩設定表單上。|  
|Backcolor|如果這個屬性設定為預設值，然後將使用使用者的色彩設定表單上。|  
|BackgroundImage|此屬性留讓文字更容易閱讀。|  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：建立 Windows 架構的協助工具應用程式](walkthrough-creating-an-accessible-windows-based-application.md)
