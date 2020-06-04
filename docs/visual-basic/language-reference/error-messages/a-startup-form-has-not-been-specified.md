---
title: 尚未指定啟動表單
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 058deb1378ed9218274ae20c8340178f7c8fa58c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409903"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="15af6-102">尚未指定啟動表單</span><span class="sxs-lookup"><span data-stu-id="15af6-102">A startup form has not been specified</span></span>

<span data-ttu-id="15af6-103">應用程式會使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別，但不會指定啟動表單。</span><span class="sxs-lookup"><span data-stu-id="15af6-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="15af6-104">如果已在 [專案設計工具] 中選取 [**啟用應用程式架構**] 核取方塊，但未指定**啟動表單**，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="15af6-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="15af6-105">如需詳細資訊，請參閱 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="15af6-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15af6-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="15af6-106">To correct this error</span></span>  
  
1. <span data-ttu-id="15af6-107">指定應用程式的啟始物件。</span><span class="sxs-lookup"><span data-stu-id="15af6-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="15af6-108">如需詳細資訊，請參閱 [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="15af6-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="15af6-109">覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> 方法，將 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> 屬性設定為啟動表單。</span><span class="sxs-lookup"><span data-stu-id="15af6-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15af6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15af6-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="15af6-111">Visual Basic 應用程式模型概觀</span><span class="sxs-lookup"><span data-stu-id="15af6-111">Overview of the Visual Basic Application Model</span></span>](../../developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
