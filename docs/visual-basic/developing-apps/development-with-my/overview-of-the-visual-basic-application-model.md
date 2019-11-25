---
title: Visual Basic 應用程式模型概觀
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application object [Visual Basic], Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
ms.openlocfilehash: aa47304cf2bded93bdb95ffe7dfa35bb37d9a643
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976465"
---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic 應用程式模型概觀

Visual Basic 提供定義完善的模型來控制 Windows Forms 應用程式的行為： Visual Basic 應用程式模型。 此模型包含處理應用程式啟動和關閉的事件，以及用來攔截未處理之例外狀況的事件。 它也提供開發單一實例應用程式的支援。 應用程式模型是可擴充的，因此需要更多控制的開發人員可以自訂其可覆寫的方法。  
  
## <a name="uses-for-the-application-model"></a>應用程式模型的使用  

 一般應用程式必須在啟動和關閉時執行工作。 例如，當它啟動時，應用程式可以顯示啟動顯示畫面、進行資料庫連接、載入儲存的狀態等等。 當應用程式關閉時，它可以關閉資料庫連接、儲存目前狀態等等。 此外，當應用程式意外關閉時，應用程式可以執行特定程式碼，例如在未處理的例外狀況期間。  
  
 Visual Basic 應用程式模型可讓您輕鬆地建立*單一實例*應用程式。 單一實例的應用程式與一般應用程式不同之處在于，一次只能執行一個應用程式實例。 嘗試啟動單一實例應用程式的另一個實例，會導致原始實例收到通知（藉由 `StartupNextInstance` 事件），也就是另一次啟動嘗試。 通知會包含後續實例的命令列引數。 接著，應用程式的後續實例會先關閉，然後才可以進行任何初始化。  
  
 單一實例應用程式會啟動，並檢查它是否為應用程式的第一個實例或後續的實例：  
  
- 如果它是第一個實例，則會如往常般啟動。  
  
- 後續每次嘗試啟動應用程式時，第一個實例執行時，會產生非常不同的行為。 後續的嘗試會通知第一個實例有關命令列引數，然後立即結束。 第一個實例會處理 `StartupNextInstance` 事件，以判斷後續實例的命令列引數為何，並繼續執行。  
  
     下圖顯示後續的實例如何指示第一個實例：  
  
     ![顯示單一實例應用程式影像的圖表。](./media/overview-of-the-visual-basic-application-model/single-instance-application.gif)  
  
 藉由處理 `StartupNextInstance` 事件，您可以控制單一實例應用程式的行為。 例如，Microsoft Outlook 通常會以單一實例應用程式的方式執行;當 Outlook 正在執行，而且您嘗試重新開機 Outlook 時，焦點會轉移至原始實例，但另一個實例則不會開啟。  
  
## <a name="events-in-the-application-model"></a>應用程式模型中的事件  

 在應用程式模型中可以找到下列事件：  
  
- **應用程式啟動**。 應用程式啟動時，會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。 藉由處理這個事件，您可以加入程式碼，在載入主要表單之前初始化應用程式。 如有需要，`Startup` 事件也會提供在啟動進程的該階段取消應用程式的執行。  
  
     您可以將應用程式設定為在應用程式啟動程式碼執行時顯示啟動顯示畫面。 根據預設，當使用 `/nosplash` 或 `-nosplash` 命令列引數時，應用程式模型會抑制啟動顯示畫面。  
  
- **單一實例應用程式**。 當單一實例應用程式的後續實例啟動時，就會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> 事件。 事件會傳遞後續實例的命令列引數。  
  
- **未處理的例外**狀況。 如果應用程式遇到未處理的例外狀況，就會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。 該事件的處理常式可以檢查例外狀況，並決定是否要繼續執行。  
  
     在某些情況下，不會引發 `UnhandledException` 事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。  
  
- **網路連接變更**。 如果電腦的網路可用性變更，應用程式就會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> 事件。  
  
     在某些情況下，不會引發 `NetworkAvailabilityChanged` 事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。  
  
- **應用程式已關閉**。 應用程式會提供 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件，以便在即將關閉時發出信號。 在該事件處理常式中，您可以確定應用程式必須執行的作業（例如，關閉和儲存）已完成。 您可以設定應用程式在主表單關閉時關閉，或只在所有表單關閉時關閉。  
  
## <a name="availability"></a>可用性  

 根據預設，Visual Basic 應用程式模型適用于 Windows Forms 專案。 如果您將應用程式設定為使用不同的啟始物件，或使用自訂 `Sub Main`啟動應用程式程式碼，則該物件或類別可能需要提供 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別的執行，才能使用應用程式模型。 如需變更啟始物件的詳細資訊，請參閱[專案設計工具、應用程式頁面（Visual Basic）](/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
