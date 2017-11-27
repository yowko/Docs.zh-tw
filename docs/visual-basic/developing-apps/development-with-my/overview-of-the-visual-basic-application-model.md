---
title: "Visual Basic 應用程式模型概觀"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b0e01317a6dab18ea03047c146def32b5675ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic 應用程式模型概觀
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供完善的模型，可控制 Windows Form 應用程式的行為：[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]應用程式模型。 此模型包含處理應用程式的啟動和關機，以及攔截未處理的例外狀況事件的事件。 它也會提供開發的單一執行個體的應用程式的支援。 應用程式模型，所以需要更多控制的開發人員可以自訂的覆寫方法。  
  
## <a name="uses-for-the-application-model"></a>使用應用程式模型  
 一般的應用程式需要執行工作，當它啟動及關機。 例如，在啟動時應用程式可以顯示啟動顯示畫面、 建立資料庫的連接、 載入已儲存的狀態，等等。 當應用程式關閉時，它可以關閉資料庫連接，儲存目前的狀態，並以此類推。 此外，應用程式可以執行特定程式碼應用程式關閉時向下意外，例如在期間處理的例外狀況。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]應用程式模型讓您輕鬆地建立*單一執行個體*應用程式。 單一執行個體的應用程式與從一般應用程式中，只有一個執行個體的應用程式可以執行一次。 嘗試啟動另一個執行個體的單一執行個體的應用程式會產生通知的原始執行個體，藉由`StartupNextInstance`事件 —，另一個啟動嘗試。 通知內容包括後續執行個體的命令列引數。 後續的執行個體的應用程式之後就關閉，然後才能進行任何初始化。  
  
 單一執行個體的應用程式啟動，並檢查是否為第一個執行個體或應用程式的後續執行個體：  
  
-   如果是第一個執行個體，如往常般啟動。  
  
-   每個後續嘗試啟動應用程式中，第一個執行個體執行時，會產生非常不同的行為。 後續嘗試通知有關命令列引數，第一個執行個體，並立即結束。 第一個執行個體控制代碼`StartupNextInstance`事件，以判斷後續執行個體的命令列引數，以及繼續執行。  
  
     這個圖表可顯示的後續的執行個體發出第一個執行個體的信號。  
  
     ![單一執行個體應用程式映像](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 藉由處理`StartupNextInstance`事件，您可以控制應用程式的單一執行個體的行為。 例如，Microsoft Outlook 通常會執行為單一執行個體應用程式。當 Outlook 執行，而且您嘗試啟動 Outlook 同樣地，焦點會轉移到原始執行個體，但不會開啟另一個執行個體。  
  
## <a name="events-in-the-application-model"></a>應用程式模型中的事件  
 應用程式模型中找到下列事件：  
  
-   **應用程式啟動**。 應用程式引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>啟動時的事件。 藉由處理這個事件，您可以加入主要表單在載入之前初始化應用程式的程式碼。 `Startup`事件也會提供取消執行階段期間之應用程式的啟動程序，如有需要。  
  
     您可以設定應用程式的應用程式啟動程式碼執行時顯示啟動顯示畫面。 根據預設，應用程式模型會隱藏啟動顯示畫面時請`/nosplash`或`-nosplash`使用命令列引數。  
  
-   **單一執行個體的應用程式**。 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>後續的執行個體的單一執行個體的應用程式啟動時，就會引發事件。 這個事件會傳遞後續的執行個體的命令列引數。  
  
-   **未處理例外狀況**。 如果應用程式遇到未處理的例外狀況，則會引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>事件。 該事件的處理常式可以檢查例外狀況，並判斷是否要繼續執行。  
  
     `UnhandledException`在某些情況下不會引發事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。  
  
-   **網路連線變更**。 如果電腦的網路可用性變更時，應用程式就會引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>事件。  
  
     `NetworkAvailabilityChanged`在某些情況下不會引發事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。  
  
-   **應用程式關閉**。 應用程式提供<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>即將關閉時發出信號的事件。 在該事件處理常式，您可以確保，操作您的應用程式需要執行 — 關閉和儲存，例如，會完成。 您可以設定應用程式關閉時，主要表單關閉，或關閉只關閉所有表單。  
  
## <a name="availability"></a>可用性  
 根據預設，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]應用程式模型僅適用於 Windows Form 專案。 如果您設定應用程式使用不同的啟動物件，或啟動應用程式程式碼與自訂`Sub Main`、 然後該物件或類別可能需要提供的實作<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>類別，才能使用應用程式模型。 如需變更啟始物件的詳細資訊，請參閱[應用程式] 頁面上，[專案設計工具 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
