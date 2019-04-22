---
title: Visual Basic 應用程式模型概觀
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: 02cc71dbda47d078284d9a2ec07538dfa063ac75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819758"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic 應用程式模型概觀
Visual Basic 提供定義完善的模型，可用於控制 Windows Forms 應用程式的行為： 在 Visual Basic 應用程式模型。 此模型包含事件處理應用程式的啟動和關機，以及攔截未處理的例外狀況的事件。 它也會提供單一執行個體的應用程式的開發的支援。 應用程式模型，所以需要更多控制的開發人員可以自訂其可覆寫的方法。  
  
## <a name="uses-for-the-application-model"></a>使用應用程式模型  
 一般的應用程式需要它啟動和關閉時執行工作。 比方說，當它啟動時，應用程式可以顯示啟動顯示畫面、 建立資料庫的連接、 載入已儲存的狀態，等等。 當應用程式關閉時，它可以關閉資料庫連接、 儲存目前的狀態，等等。 此外，應用程式可以執行特定程式碼應用程式關閉時向下意外，例如期間處理的例外狀況。  
  
 Visual Basic 應用程式模型可讓您輕鬆地建立*單一執行個體*應用程式。 單一執行個體的應用程式與從一般的應用程式中，只有一個執行個體的應用程式可以執行一次。 嘗試啟動另一個執行個體的單一執行個體的應用程式會產生通知的原始執行個體，藉由`StartupNextInstance`事件 —，另一個啟動嘗試。 這個通知會包含於後續執行個體的命令列引數。 後續的執行個體的應用程式之後就關閉，才能進行任何初始化。  
  
 單一執行個體的應用程式會啟動，並檢查是否為第一個執行個體或應用程式的後續執行個體：  
  
-   如果是第一個執行個體，它會開始如往常般。  
  
-   若要啟動應用程式，第一個執行個體執行時，每個後續的嘗試會導致非常不同的行為。 後續的嘗試通知有關命令列引數，第一個執行個體，然後立即結束。 第一個執行個體控制代碼`StartupNextInstance`事件，以判斷哪些後續的執行個體的命令列引數，並繼續執行。  
  
     下圖顯示後續的執行個體發出第一個執行個體的訊號：  
  
     ![此圖顯示單一執行個體的應用程式映像。](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 藉由處理`StartupNextInstance`事件，您可以控制您的單一執行個體應用程式的運作方式。 例如，Microsoft Outlook 通常會執行為單一執行個體應用程式;當 Outlook 正在執行，而且您嘗試啟動 Outlook 同樣地，焦點會轉移到原始執行個體，但不會開啟另一個執行個體。  
  
## <a name="events-in-the-application-model"></a>應用程式模型中的事件  
 應用程式模型中找到下列事件：  
  
-   **應用程式啟動**。 應用程式引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>啟動時的事件。 藉由處理這個事件，您可以加入主要表單載入之前初始化應用程式的程式碼。 `Startup`事件也會提供取消執行階段期間的應用程式啟動程序，如有需要。  
  
     您可以設定應用程式啟動程式碼執行時顯示啟動顯示畫面的應用程式。 根據預設，應用程式模型會隱藏啟動顯示畫面時請`/nosplash`或`-nosplash`使用命令列引數。  
  
-   **單一執行個體的應用程式**。 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>後續的執行個體的單一執行個體的應用程式啟動時，會引發事件。 這個事件會傳遞後續的執行個體的命令列引數。  
  
-   **未處理例外狀況**。 如果應用程式遇到未處理的例外狀況，則會引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>事件。 您針對該事件的處理常式可以檢查例外狀況，並判斷是否要繼續執行。  
  
     `UnhandledException`在某些情況下不會引發事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。  
  
-   **網路連線能力變更**。 如果電腦的網路可用性變更時，應用程式就會引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>事件。  
  
     `NetworkAvailabilityChanged`在某些情況下不會引發事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。  
  
-   **應用程式關閉**。 應用程式提供<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>事件，以表示它即將關閉時。 在該事件處理常式中，您可以確保，操作您的應用程式需要執行 — 關閉並儲存，例如，已完成。 您可以設定您的應用程式關閉時關閉主要表單，或關閉只有當所有的表單關閉。  
  
## <a name="availability"></a>可用性  
 根據預設，Visual Basic 應用程式模型可供 Windows Form 專案。 如果您設定應用程式使用不同的啟動物件，或自訂的應用程式程式碼的開頭`Sub Main`，然後該物件或類別可能需要提供的實作<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>類別使用的應用程式模型。 如需變更啟始物件的詳細資訊，請參閱 < [Application Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
