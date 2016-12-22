---
title: "Overview of the Visual Basic Application Model | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Application object, Visual Basic application model"
  - "Visual Basic application model"
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overview of the Visual Basic Application Model
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 會提供妥善定義的模型，用於控制 Windows Form 應用程式的行為：[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 應用程式模型。  此模型會包含用於處理應用程式啟動與關閉的事件，以及用於攔截未處理之例外狀況的事件。  它也支援開發單一執行個體應用程式。  應用程式模型是可延伸的，因此需要更多控制的開發人員可以自訂此模型的覆寫方法。  
  
## 用於應用程式模型  
 應用程式通常需要在它啟動或關閉時執行工作。  例如，在啟動應用程式時，顯示啟動顯示畫面、與資料庫連線、載入儲存狀態等等。  當應用程式關閉時，會關閉資料庫連線、儲存目前的狀態等等。  此外，應用程式還會在應用程式意外關閉時 \(例如，在未處理的例外狀況期間\) 執行特定的程式碼。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 應用程式模型讓建立「*單一執行個體*」\(Single\-instance\) 應用程式的工作變得更容易。  單一執行個體應用程式與正常應用程式不同的地方是，它一次只能執行一個應用程式執行個體。  如果嘗試啟動單一執行個體應用程式的另一個執行個體，則會利用 `StartupNextInstance` 事件通知原始的執行個體，告知已嘗試另一個啟動作業。  此通知會包含後續執行個體的命令列引數。  然後，應用程式的後續執行個體會在發生任何初始設定之前關閉。  
  
 單一執行個體應用程式會啟動，並檢查它是第一個執行個體，還是應用程式的後續執行個體：  
  
-   如果是第一個執行個體，則照例啟動它。  
  
-   當第一個執行個體執行時，要啟動應用程式的每一個後續嘗試都會有不同的行為。  後續嘗試會通知第一個執行個體相關的命令列引數，然後立刻結束。  第一個執行個體會處理 `StartupNextInstance` 事件，判斷後續執行個體的命令列引數為何，再繼續執行。  
  
     本圖表會顯示後續執行個體如何通知第一個執行個體。  
  
     ![單一執行個體應用程式影像](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 藉由處理 `StartupNextInstance` 事件，您可以控制單一執行個體應用程式行為表現的方式。  例如，Microsoft Outlook 通常會以單一執行個體應用程式執行，當 Outlook 正在執行時，若您嘗試重新啟動 Outlook，焦點便會轉移到原始的執行個體，但不會開啟另一個執行個體。  
  
## 應用程式模型中的事件  
 下列事件可以在應用程式模型中找到：  
  
-   **應用程式啟動**：  應用程式會在它啟動時引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。  藉由處理此事件，您可以在載入主要表單之前加入初始化應用程式的程式碼。  `Startup` 事件也會視需要在啟動處理序的階段期間取消應用程式的執行。  
  
     您可以設定應用程式在應用程式啟動程式碼執行時顯示啟動顯示畫面。  根據預設，應用程式模型會在使用 `/nosplash` 或 `-nosplash` 命令列引數時隱藏啟動顯示畫面。  
  
-   **單一執行個體應用程式**：  單一執行個體應用程式的後續執行個體啟動時，會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> 事件。  事件會傳遞後續執行個體的命令列引數。  
  
-   **未處理的例外狀況**：  如果應用程式遇到未處理的例外狀況，會產生 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。  該事件的處理常式會檢查例外狀況，並判斷是否要繼續執行。  
  
     在某些情況下不會引發 `UnhandledException` 事件。  如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。  
  
-   **網路連接變更**：  如果電腦的網路連接變更，應用程式會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> 事件。  
  
     在某些情況下不會引發 `NetworkAvailabilityChanged` 事件。  如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。  
  
-   **應用程式關閉**：  應用程式會提供 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件，在它即將關閉時送出信號。  在該事件處理常式中，您可以確定應用程式需要執行的作業 \(例如，關閉與儲存\) 已完成。  您可以設定應用程式在主要表單關閉時關閉，或是只在所有表單都關閉時才關閉。  
  
## 可用性  
 根據預設，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 應用程式模型可供 Windows Form 專案使用。  如果您設定應用程式會使用不同的啟始物件，或是以自訂的 `Sub Main` 啟動應用程式的程式碼，那麼物件或類別可能需要提供 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別的實作，以使用應用程式模型。  如需變更啟始物件的詳細資訊，請參閱 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)