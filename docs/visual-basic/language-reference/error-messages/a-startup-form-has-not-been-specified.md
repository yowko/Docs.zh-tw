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
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="7c4ed-102">尚未指定啟動表單</span><span class="sxs-lookup"><span data-stu-id="7c4ed-102">A startup form has not been specified</span></span>
<span data-ttu-id="7c4ed-103">應用程式使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>類別，但未指定啟動表單。</span><span class="sxs-lookup"><span data-stu-id="7c4ed-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="7c4ed-104">這種情形**啟用應用程式架構** 核取方塊已選取專案設計工具中，但**啟動表單**未指定。</span><span class="sxs-lookup"><span data-stu-id="7c4ed-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="7c4ed-105">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="7c4ed-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c4ed-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7c4ed-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7c4ed-107">指定應用程式的啟動物件。</span><span class="sxs-lookup"><span data-stu-id="7c4ed-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="7c4ed-108">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="7c4ed-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="7c4ed-109">覆寫<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>方法來設定<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>啟動表單的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c4ed-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4ed-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c4ed-110">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="7c4ed-111">Visual Basic 應用程式模型概觀</span><span class="sxs-lookup"><span data-stu-id="7c4ed-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
