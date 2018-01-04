---
title: "如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7b6f8ff44763c19de1eac6d4be98bca75ff9f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>如何：使用設計工具將 Windows Form 按鈕指定為接受按鈕
您可以在任何 Windows 表單上，指定<xref:System.Windows.Forms.Button>控制項為接受按鈕，也稱為預設按鈕。 每當使用者按下 ENTER 鍵，是按下無論哪個表單上的其他控制項具有焦點的預設按鈕。 例外狀況是另一個按鈕具有焦點的控制項時，會在此情況下，按一下具有焦點按鈕，或多行文字方塊中或自訂控制項的 ENTER 鍵。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-designate-the-accept-button"></a>若要指定接受按鈕  
  
1.  選取按鈕所在的表單。  
  
2.  在**屬性**視窗中，將表單的<xref:System.Windows.Forms.Form.AcceptButton%2A>屬性<xref:System.Windows.Forms.Button>控制項的名稱。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Button 控制項概觀](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [選取 Windows Forms Button 控制項的方法](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [操作說明：回應 Windows Forms Button 按一下動作](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [操作說明：使用設計工具將 Windows Forms 按鈕指定為取消按鈕](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Button 控制項](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
