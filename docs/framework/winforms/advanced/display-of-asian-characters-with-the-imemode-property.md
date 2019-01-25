---
title: 使用 ImeMode 屬性顯示亞洲字元
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500511"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>使用 ImeMode 屬性顯示亞洲字元
<xref:System.Windows.Forms.Control.ImeMode%2A>屬性用表單和控制項來強制執行特定模式的輸入的法編輯器 (IME)。 IME 是撰寫中文、日文和韓文字的重要元件，因為這些書寫系統的字元數比可以為一般鍵盤編碼的字元數還要多。 例如，您可能只要在特定文字方塊中允許 ASCII 字元。 在此情況下您可以設定<xref:System.Windows.Forms.Control.ImeMode%2A>屬性設<xref:System.Windows.Forms.ImeMode>使用者僅能為該特定文字方塊中輸入 ASCII 字元。 預設值<xref:System.Windows.Forms.Control.ImeMode%2A>屬性是<xref:System.Windows.Forms.ImeMode>，因此如果您設定表單的屬性時，表單上的所有控制項都會都繼承該設定。 如需詳細資訊，請參閱 < <xref:System.Windows.Forms.Control.ImeMode%2A> ) 和<xref:System.Windows.Forms.ImeMode>。  
  
## <a name="see-also"></a>另請參閱

- [全球化 Windows Forms 應用程式](globalizing-windows-forms.md)
