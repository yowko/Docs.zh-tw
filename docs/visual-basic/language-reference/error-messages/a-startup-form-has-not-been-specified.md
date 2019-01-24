---
title: 尚未指定啟動表單
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: f05358f76829768d8ff5c4ac85b5134f35254126
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627209"
---
# <a name="a-startup-form-has-not-been-specified"></a>尚未指定啟動表單
應用程式使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>類別，但未指定啟動表單。  
  
 這種情形**啟用應用程式架構** 核取方塊已選取專案設計工具中，但**啟動表單**未指定。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  指定應用程式的啟動物件。  
  
     如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
2.  覆寫<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>方法來設定<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>啟動表單的屬性。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visual Basic 應用程式模型概觀](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
