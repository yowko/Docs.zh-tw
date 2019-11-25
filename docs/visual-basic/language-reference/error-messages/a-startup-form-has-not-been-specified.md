---
title: 尚未指定啟動表單
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 301f249e6222c929d2c513964ecbb21df5fbc47f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976185"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="857be-102">尚未指定啟動表單</span><span class="sxs-lookup"><span data-stu-id="857be-102">A startup form has not been specified</span></span>

<span data-ttu-id="857be-103">應用程式會使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別，但不會指定啟動表單。</span><span class="sxs-lookup"><span data-stu-id="857be-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="857be-104">如果已在 [專案設計工具] 中選取 [**啟用應用程式架構**] 核取方塊，但未指定**啟動表單**，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="857be-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="857be-105">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="857be-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="857be-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="857be-106">To correct this error</span></span>  
  
1. <span data-ttu-id="857be-107">指定應用程式的啟始物件。</span><span class="sxs-lookup"><span data-stu-id="857be-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="857be-108">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="857be-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="857be-109">覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> 方法，將 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> 屬性設定為啟動表單。</span><span class="sxs-lookup"><span data-stu-id="857be-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="857be-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="857be-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="857be-111">Visual Basic 應用程式模型概觀</span><span class="sxs-lookup"><span data-stu-id="857be-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
