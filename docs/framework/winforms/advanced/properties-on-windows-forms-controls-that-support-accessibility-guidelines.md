---
title: 控制項的協助工具屬性
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: 73d81f5b5f656ed5ef90bdd9b6fe1b3293123f97
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743431"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>支援可及性方針的 Windows Form 控制項屬性
Windows Forms 的標準工具箱上的控制項支援許多協助工具方針，包括公開鍵盤焦點及公開螢幕元素。  
  
## <a name="planning-ahead-for-accessibility"></a>向前規劃協助工具  
 控制項的屬性可以用來支援其他協助工具方針，如下表所示。 此外，您應該使用功能表來提供程式功能的存取權。  
  
|控制項屬性|協助工具的考慮|  
|----------------------|--------------------------------------|  
|AccessibleDescription|描述會回報給協助工具輔助，例如螢幕讀取器。 協助工具是特製化的程式和裝置，可以協助殘障人士更有效地使用電腦。|  
|AccessibleName|將報告給協助工具輔助的名稱。|  
|AccessibleRole|描述在使用者介面中使用元素的方式。|  
|TabIndex|透過表單建立合理的導覽路徑。 對於沒有內建標籤的控制項（例如文字方塊）而言，其相關聯的標籤會立即在定位順序中的前面加上，這是很重要的。|  
|Text|使用 "&" 字元來建立存取金鑰。 使用存取金鑰是提供已記載的鍵盤存取功能的一部分。|  
|字型大小|如果無法調整字型大小，則應該將它設定為10點或更大的值。 一旦設定表單的字型大小，此後加入表單的所有控制項都會有相同的大小。|  
|Forecolor|如果此屬性設為預設值，則會在表單上使用使用者的色彩喜好設定。|  
|Backcolor|如果此屬性設為預設值，則會在表單上使用使用者的色彩喜好設定。|  
|BackgroundImage|將此屬性保留空白，讓文字更容易閱讀。|  
  
## <a name="see-also"></a>另請參閱

- [逐步解說：建立 Windows 架構的協助工具應用程式](walkthrough-creating-an-accessible-windows-based-application.md)
