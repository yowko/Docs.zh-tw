---
title: "Visual Basic 應用程式模型概觀 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application object, Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0925bb102c148480d82128b91cbf1762de24e7ec
ms.lasthandoff: 03/13/2017

---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic 應用程式模型概觀
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供定義完善的模型，可控制 Windows Form 應用程式的行為︰[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式模型。 此模型包含用於處理應用程式的啟動和關機，以及攔截未處理的例外狀況的事件。 它也會提供開發單一執行個體應用程式的支援。 應用程式模型，所以需要更多控制的開發人員可以自訂的覆寫方法。  
  
## <a name="uses-for-the-application-model"></a>使用應用程式模型  
 一般應用程式需要它啟動和關閉時執行工作。 比方說，它在啟動時，應用程式可以顯示開頭顯示畫面、 資料庫連線、 載入已儲存的狀態等等。 當應用程式關閉時，它可以關閉資料庫連接、 儲存目前的狀態，並以此類推。 此外，應用程式可以執行特定程式碼時，即應用程式向下意外，例如在期間處理的例外狀況。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式模型讓您輕鬆地建立*單一執行個體*應用程式。 單一執行個體的應用程式與一般應用程式中，只有一個執行個體的應用程式可以執行一次。 嘗試啟動另一個執行個體的單一執行個體應用程式會導致不會收到通知的原始執行個體，藉由`StartupNextInstance`事件 —，另一個啟動嘗試。 通知內容包括後續的執行個體的命令列引數。 發生任何初始設定之前，之後就會關閉應用程式的後續的執行個體。  
  
 單一執行個體應用程式啟動，並檢查是否為第一個執行個體或應用程式的後續執行個體︰  
  
-   如果是第一個執行個體，同時也會如往常般。  
  
-   每一個後續嘗試啟動應用程式，而第一個執行個體執行時，會導致非常不同的行為。 後續的嘗試通知有關命令列引數，第一個執行個體，然後立即結束。 第一個執行個體控制代碼`StartupNextInstance`事件，以決定後續執行個體的命令列引數，以及會繼續執行。  
  
     這個圖表顯示後續的執行個體如何通知第一個執行個體。  
  
     ![單一執行個體應用程式映像](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 藉由處理`StartupNextInstance`事件，您可以控制應用程式的單一執行個體的行為。 例如，Microsoft Outlook 通常會執行為單一執行個體應用程式。當 Outlook 正在執行，而且您嘗試啟動 Outlook 同樣地，焦點會轉移到原始執行個體，但不會開啟另一個執行個體。  
  
## <a name="events-in-the-application-model"></a>應用程式模型中的事件  
 應用程式模型中找到下列事件︰  
  
-   **應用程式啟動**。 應用程式引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>事件時啟動。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 藉由處理這個事件，您可以加入主要表單載入之前初始化應用程式的程式碼。 `Startup`事件也會提供取消執行階段期間的應用程式啟動程序，如有需要。  
  
     您可以設定應用程式的應用程式啟動程式碼執行時顯示開頭顯示畫面。 根據預設，應用程式模型會隱藏啟動顯示畫面時可能是`/nosplash`或`-nosplash`使用命令列引數。  
  
-   **單一執行個體的應用程式**。 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>後續的執行個體的單一執行個體應用程式啟動時，會引發事件。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> 這個事件會傳遞後續的執行個體的命令列引數。  
  
-   **未處理例外狀況**。 如果應用程式遇到未處理的例外狀況，則會引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>事件。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 該事件的處理常式可以檢查例外狀況，並判斷是否要繼續執行。  
  
     `UnhandledException`在某些情況下不會引發事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>  
  
-   **網路連線變更**。 如果電腦的網路狀態變更時，應用程式就會引發<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>事件。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
  
     `NetworkAvailabilityChanged`在某些情況下不會引發事件。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>  
  
-   **應用程式關閉**。 應用程式提供<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>事件發出信號即將關閉時。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 在該事件處理常式中，您可以確保，操作您的應用程式需要執行 — 關閉和儲存，例如，已完成。 您可以設定應用程式關閉時，主要表單關閉，或關閉只關閉所有表單。  
  
## <a name="availability"></a>可用性  
 根據預設，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式模型是適用於 Windows Form 專案。 如果您設定應用程式使用不同的啟動物件，或開始自訂應用程式程式碼`Sub Main`，然後該物件或類別可能需要提供的實作<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>類別來使用應用程式模型。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 變更啟始物件的相關資訊，請參閱[應用程式] 頁面上，[專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [擴充 Visual Basic 應用程式模型](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
