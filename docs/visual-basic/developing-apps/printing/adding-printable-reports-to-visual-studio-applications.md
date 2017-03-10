---
title: "Adding Printable Reports to Visual Studio Applications | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "printing [Visual Studio], reports"
  - "reports, printing in Visual Studio"
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Adding Printable Reports to Visual Studio Applications
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Studio 支援各種報表方案，可以協助您將內容豐富的資料報表加入至 Visual Basic 應用程式。  您可以使用 ReportViewer 控制項、Crystal Reports 或 SQL Server Reporting Services 來建立並加入報表。  
  
> [!NOTE]
>  SQL Server Reporting Services 屬於 SQL Server 2005 的一部分，而非 Visual Studio。  除非您已經安裝 SQL Server 2005，否則系統上不會安裝 Reporting Services。  
  
## Visual Basic 應用程式中的 Microsoft 報表技術概觀  
 請從下列選擇在應用程式中使用 Microsoft 報表技術的方式：  
  
-   將 ReportViewer 控制項的一個或多個執行個體 \(Instance\) 加入至 Visual Basic Windows 應用程式。  
  
-   藉由呼叫報表伺服器 Web 服務，以程式設計方式整合 SQL Server Reporting Services。  
  
-   將 ReportViewer 控制項與 Microsoft SQL Server 2005 Reporting Services 一起搭配使用，並將控制項當做報表檢視器，將報表伺服器當做報表處理器   \(請注意，如果您想要將報表伺服器與 ReportViewer 控制項一起搭配使用，必須使用 SQL Server 2005 版的 Reporting Services\)。  
  
## 使用 ReportViewer 控制項  
 如果想要將報表功能內嵌於 Visual Basic Windows 應用程式中，最簡單的方式就是將 ReportViewer 控制項加入至應用程式中的表單。  控制項會將報表處理功能直接加入至應用程式，並提供整合式報表設計工具，讓您能夠使用任何 ADO.NET 資料物件中的資料來建置 \(Build\) 報表。  具有完整功能的 API 可讓您以程式設計方式存取控制項和報表，進而可以設定執行階段功能。  
  
 ReportViewer 在單一、可任意散發的資料控制項中提供了內建的報表處理和檢視功能。  如果您需要下列報表功能，請選擇 ReportViewer 控制項：  
  
-   用戶端應用程式中的報表處理。  處理過的報表會顯示在控制項所提供的檢視區域中。  
  
-   對 ADO.NET 資料表的資料繫結 \(Data Binding\)。  您可以建立報表，使用為控制項提供的 <xref:System.Data.DataTable> 執行個體。  您也可以直接繫結至商務物件 \(Business Object\)。  
  
-   可以包含在應用程式中的可轉散發控制項。  
  
-   執行階段功能，例如頁面巡覽、列印、搜尋和匯出格式。  ReportViewer 工具列會提供這些作業的支援。  
  
 若要使用 ReportViewer 控制項，可以將它從 Visual Studio 工具箱的 \[**資料**\] 區域，拖曳至 Visual Basic Windows 應用程式中的表單上。  
  
### 在 Visual Studio 中建立適用於 ReportViewer 控制項的報表  
 若要建置可在 ReportViewer 中執行的報表，請將 \[**報表**\] 範本加入至專案。  Visual Studio 會建立用戶端報表定義檔案 \(.rdlc\)、將檔案加入至專案，然後在 Visual Studio 工作區 \(Workspace\) 中開啟整合式報表設計工具。  
  
 Visual Studio 報表設計工具會與 \[**資料來源**\] 視窗整合。  當您將欄位從 \[**資料來源**\] 視窗拖曳至報表時，報表設計工具會將資料來源的相關中繼資料 \(Metadata\) 複製到報表定義檔案中。  ReportViewer 控制項會使用此中繼資料，自動產生資料繫結程式碼。  
  
 Visual Studio 報表設計工具不包含報表預覽功能。  若要預覽報表，請執行應用程式並預覽內嵌於應用程式中的報表。  
  
||  
|-|  
|若要將基本報表功能加入至應用程式|  
|1.  將 ReportViewer 控制項從 \[**工具箱**\] 的 \[**資料**\] 索引標籤中拖曳至表單上。<br />2.  在 \[**專案**\] 功能表中，選擇 \[**加入新項目**\]。  在 \[**加入新項目**\] 對話方塊中，選取 \[**報表**\] 圖示，然後按一下 \[**加入**\]。<br />     報表設計工具便會在開發環境中開啟，並且將報表檔案 \(.rdlc\) 加入至專案。<br />3.  將報表項目從 \[**工具箱**\] 中拖曳至報表配置上，並依照需要加以排列。<br />4.  將欄位從 \[**資料來源**\] 視窗中拖曳至報表配置中的報表項目。|  
  
## 在 Visual Basic 應用程式中使用 Reporting Services  
 Reporting Services 是 SQL Server 中所包含的伺服器報表技術。  Reporting Services 包含了 ReportViewer 控制項中所沒有的其他功能。  如果您需要下列任何功能，請選擇 Reporting Services：  
  
-   擴充部署和伺服器端報表處理，可針對較複雜或執行時間較長的報表以及數量龐大的報表活動改善效能。  
  
-   整合式的資料和報表處理，並且支援自訂的報表控制項和豐富的轉譯輸出格式。  
  
-   排程的報表處理，讓您能夠精確地指定報表的執行時間。  
  
-   透過電子郵件將報表直接發佈給訂閱者，或是發佈至檔案共用位置。  
  
-   臨機操作 \(Ad Hoc\) 報表，讓商務使用者可以依照需要建立報表。  
  
-   資料驅動的訂閱方式，將自訂的報表輸出傳送至動態的收件者清單。  
  
-   資料處理、報表傳送、自訂驗證和報表轉譯的自訂擴充功能。  
  
 報表伺服器是以 Web 服務的方式實作。  您的應用程式程式碼必須包含 Web 服務的呼叫，才能存取報表和其他中繼資料。  Web 服務提供了完整的存取功能，可讓您以程式設計方式存取報表伺服器執行個體。  
  
 由於 Reporting Services 是 Web 架構的報表技術，因此預設的檢視器會顯示轉譯為 HTML 格式的報表。  如果您不想使用 HTML 做為預設的報表呈現格式，則必須為應用程式撰寫自訂的報表檢視器。  
  
### 在 Visual Studio 中建立適用於 Reporting Services 的報表  
 若要建置可在報表伺服器上執行的報表，請透過 SQL Server 2005 中所提供的 Business Intelligence Development Studio，在 Visual Studio 中建立報表定義檔案 \(.rdl\)。  
  
> [!NOTE]
>  您必須安裝 SQL Server 2005，才能使用 SQL Server Reporting Services 和 Business Intelligence Development Studio。  
  
 Business Intelligence Development Studio 會加入 SQL Server 元件特有的專案範本。  若要建立報表，可以從 \[**報表伺服器專案**\] 或 \[**報表伺服器專案精靈**\] 範本中選擇適合的範本。  您可以針對各種不同的資料來源類型指定資料來源連接和查詢，包括 SQL Server、Oracle、Analysis Services、XML 和 SQL Server Integration Services。  \[**資料**\] 索引標籤、\[**配置**\] 索引標籤和 \[**預覽**\] 索引標籤可以讓您在同一個工作區中定義資料、建立報表配置，以及預覽報表。  
  
 您為控制項或報表伺服器所建置的報表定義，可以在這兩項技術中重複使用。  
  
||  
|-|  
|若要建立可在報表伺服器上執行的報表|  
|1.  在 \[**檔案**\] 功能表上，選擇 \[**開新檔案**\]。<br />     \[**新增專案**\] 對話方塊隨即開啟。<br />2.  在 \[**專案類型**\] 窗格中，按一下 \[**商務智慧專案**\]。<br />3.  在 \[範本\] 窗格中，選取 \[**報表伺服器專案**\] 或 \[**報表伺服器專案精靈**\]。|  
  
## 將 ReportViewer 控制項與 SQL Server Reporting Services 一起搭配使用  
 ReportViewer 控制項和 SQL Server 2005 Reporting Services 可以在相同的應用程式中一起搭配使用。  
  
-   ReportViewer 控制項會提供檢視器，用來在應用程式中顯示報表。  
  
-   Reporting Services 會提供報表，並且在遠端伺服器上執行所有的處理。  
  
 ReportViewer 控制項可以設定為用來顯示在遠端 Reporting Services 報表伺服器上儲存和處理的報表。  這種類型的組態稱為「*遠端處理模式*」\(Remote Processing Mode\)。  在遠端處理模式中，控制項會要求儲存在遠端報表伺服器上的報表。  報表伺服器會執行所有的報表處理、資料處理和報表呈現。  完成且完整呈現的報表會傳回至控制項，並且顯示在檢視區域中。  
  
 可在報表伺服器上執行的報表還支援其他的匯出格式、具有不同的報表參數型實作、使用報表伺服器所支援的資料來源類型，而且是透過報表伺服器上以角色為基礎的授權模型來進行存取。  
  
 若要使用遠端處理模式，請在設定 ReportViewer 控制項時指定伺服器報表的 URL 和路徑。