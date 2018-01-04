---
title: "使用 ImeMode 屬性顯示亞洲字元"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>使用 ImeMode 屬性顯示亞洲字元
<xref:System.Windows.Forms.Control.ImeMode%2A>屬性可由表單和控制項來強制特定模式的輸入的法 (ime)。 IME 是撰寫中文、日文和韓文字的重要元件，因為這些書寫系統的字元數比可以為一般鍵盤編碼的字元數還要多。 例如，您可能只要在特定文字方塊中允許 ASCII 字元。 您可以在此情況下設定<xref:System.Windows.Forms.Control.ImeMode%2A>屬性<xref:System.Windows.Forms.ImeMode>使用者僅能為該特定的文字方塊中輸入 ASCII 字元。 預設值<xref:System.Windows.Forms.Control.ImeMode%2A>屬性是<xref:System.Windows.Forms.ImeMode>，因此如果您設定表單的屬性，在表單上的所有控制項將會都繼承該設定。 如需詳細資訊，請參閱<xref:System.Windows.Forms.Control.ImeMode%2A>) 和<xref:System.Windows.Forms.ImeMode>。  
  
## <a name="see-also"></a>請參閱  
 [全球化 Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
