---
title: 多重文件介面 (MDI) 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- forms [Windows Forms], MDI
- windows [Windows Forms], mDI
- Windows Forms, MDI applications
- MDI
ms.assetid: 599faf75-13cf-49cc-ad3c-255545e5cb97
ms.openlocfilehash: 23e0275d5e6b081ec02d669a78e8695453360637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956551"
---
# <a name="multiple-document-interface-mdi-applications"></a>多重文件介面 (MDI) 應用程式
多重文件介面 (MDI) 應用程式可讓您同時顯示多份檔, 每份檔都會顯示在自己的視窗中。 MDI 應用程式通常會有一個視窗功能表項目, 其中包含可在視窗或檔之間切換的子功能表。  
  
> [!NOTE]
> Windows Forms 中的 MDI 表單和單一檔介面 (SDI) 視窗之間有一些行為差異。 `Opacity`屬性不會影響 MDI 子表單的外觀。 此外, <xref:System.Windows.Forms.Form.CenterToParent%2A>方法不會影響 MDI 子表單的行為。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：建立 MDI 父表單](how-to-create-mdi-parent-forms.md)  
 說明如何在 MDI 應用程式中建立多個檔的容器。  
  
 [如何：建立 MDI 子表單](how-to-create-mdi-child-forms.md)  
 說明如何建立在 MDI 父表單中操作的一或多個視窗。  
  
 [如何：決定作用中的 MDI 子系](how-to-determine-the-active-mdi-child.md)  
 提供驗證具有焦點之子視窗的指示 (並將其內容傳送至剪貼簿)。  
  
 [如何：將資料傳送至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)  
 提供將資訊傳輸至作用中子視窗的指示。  
  
 [如何：排列 MDI 子表單](how-to-arrange-mdi-child-forms.md)  
 提供如何並排、串聯或排列 MDI 應用程式之子視窗的指示。
