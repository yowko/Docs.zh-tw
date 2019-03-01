---
title: 將可列印報表加入至 Visual Studio 應用程式
ms.date: 07/20/2015
helpviewer_keywords:
- printing [Visual Studio], reports
- reports [Visual Basic], printing in Visual Studio
ms.assetid: 93928405-ef41-495e-bce2-9d43d5a7080a
ms.openlocfilehash: 65264deea3aeff1a633ea6888b3f175031b7fba5
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212010"
---
# <a name="adding-printable-reports-to-visual-studio-applications"></a>將可列印報表加入至 Visual Studio 應用程式
Visual Studio 支援各種不同的報表方案，協助您將新增回報給您的 Visual Basic 應用程式的豐富資料。 您可以建立並加入使用 ReportViewer 控制項、 採用的 Crystal Reports 或 SQL Server Reporting Services 報表。  

  
## <a name="overview-of-microsoft-reporting-technology-in-visual-basic-applications"></a>Microsoft 報表技術，在 Visual Basic 應用程式的概觀  
 使用 Microsoft 報表技術，在您的應用程式中從下列方法選擇：  
  
-   Visual Basic Windows 應用程式中加入 ReportViewer 控制項的一或多個執行個體。  
  
-   以程式設計方式將 SQL Server Reporting Services 整合藉由呼叫報表伺服器 Web 服務。  
  
-   ReportViewer 控制項和 Microsoft SQL Server 2005 報告的服務一起使用，做為報表檢視器和報表伺服器使用控制項，為報表處理器。 （請注意，是否您想要一起使用的報表伺服器和 ReportViewer 控制項，您必須使用 Reporting Services 的 SQL Server 2005 版本）。  
  
## <a name="using-reportviewer-controls"></a>使用 ReportViewer 控制項  
 若要內嵌到 Visual Basic Windows 應用程式的報表功能最簡單方式是將 ReportViewer 控制項新增至您的應用程式中的表單。 此控制項將報表處理功能，直接以您的應用程式，並提供整合的報表設計工具，讓您可以建立報表使用的任何 ADO.NET 資料物件中的資料。 功能完整的 API 提供以程式設計方式存取控制項，並報告，讓您可以設定執行階段功能。  
  
 ReportViewer 提供內建的報表處理和檢視單一且任意散發的資料控制項中的功能。 選擇 ReportViewer 控制項，是否您需要下列的報表功能：  
  
-   報表處理的用戶端應用程式。 處理的報表會出現在控制項所提供的檢視區域。  
  
-   資料繫結至 ADO.NET 資料的資料表中。 您可以建立取用的報表<xref:System.Data.DataTable>提供給控制項的執行個體。 您也可以直接至商務物件繫結。  
  
-   您可以納入您的應用程式的可轉散發控制項。  
  
-   執行階段功能，例如頁面導覽、 列印、 搜尋及匯出格式。 ReportViewer 工具列提供這些作業的支援。  
  
 若要使用 ReportViewer 控制項，您可以將它從拖曳**資料**Visual Studio 工具箱拖曳至表單，以在 Visual Basic Windows 應用程式中的區段。  
  
### <a name="creating-reports-in-visual-studio-for-reportviewer-controls"></a>在 Visual Studio 中建立報表，ReportViewer 控制項  
 若要建置在 ReportViewer 中執行的報表，加入**報表**範本加入專案。 Visual Studio 會建立用戶端報表定義檔案 (.rdlc)，將檔案新增至您的專案，並在 Visual Studio 工作區中開啟整合式的報表設計師。  
  
 Visual Studio 報表設計工具整合了**Zdroje dat**視窗。 當您將欄位從**Zdroje dat**至報表，報表設計工具 視窗會將資料來源的相關中繼資料複製到報表定義檔案。 此中繼資料可由 ReportViewer 控制項來自動產生資料繫結程式碼。  
  
 Visual Studio 報表設計工具不包括報表預覽功能。 若要預覽報表、 執行應用程式和預覽報表內嵌在其中。  
  
|將基本報表功能加入您的應用程式|  
|---|    
|1.將 ReportViewer 控制項，從**資料**索引標籤**工具箱**拖曳至表單。<br />2.在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。 在 **加入新項目**對話方塊中，選取**報表**圖示，然後按一下**新增**。<br />     在開發環境中，開啟 報表設計師和報表 (.rdlc) 檔案加入至專案。<br />3.將報表項目，從**工具箱**在報表配置，並視需要加以排列。<br />4.將欄位從**Zdroje dat**報表配置中的報表項目 視窗。|  
  
## <a name="using-reporting-services-in-visual-basic-applications"></a>在 Visual Basic 應用程式中使用 Reporting Services  
 Reporting Services 是伺服器架構報告技術隨附 SQL Server。 Reporting Services 包含 ReportViewer 控制項中找不到的其他功能。 如果您需要下列功能，請選擇 Reporting Services:  
  
-   向外延展部署，而且提供更佳的效能，針對高容量報表活動的複雜或長時間執行的報表及伺服器端報表處理。  
  
-   整合式的資料和報表處理，支援自訂報表控制項和轉譯的輸出格式。  
  
-   排程報表處理，因此您可以指定執行報表的確切時間。  
  
-   透過電子郵件或檔案共用位置的訂閱者 」 為基礎的報表散發。  
  
-   隨選報表，以便視商務使用者可以建立報表。  
  
-   將自訂的報表輸出路由至收件者的動態清單的資料驅動訂閱。  
  
-   自訂資料處理、 報表傳遞、 自訂的驗證和報表轉譯的延伸模組。  
  
 報表伺服器會實作為 Web 服務。 您的應用程式程式碼必須包含對 Web 服務呼叫，以存取報表和其他中繼資料。 Web 服務提供完整的程式設計存取，報表伺服器執行個體。  
  
 由於 Reporting Services Web 為基礎的報告技術的預設檢視器會以 HTML 格式顯示轉譯的報表。 如果您不要使用 HTML 做為預設的報表呈現格式，您必須撰寫您的應用程式的自訂報表檢視器。  
  
### <a name="creating-reports-in-visual-studio-for-reporting-services"></a>在 Visual Studio 中建立報表，Reporting services  
 若要建立報表伺服器執行的報表，您建立報表定義 (.rdl) 檔案在 Visual Studio 中透過 Business Intelligence Development Studio 中，這是隨附於 SQL Server 2005。  
  
 Business Intelligence Development Studio 新增專屬於 SQL Server 元件的專案範本。 若要建立報表，您可以選擇**報表伺服器專案**或是**報表伺服器專案精靈**範本。 您可以指定資料來源連接和查詢，以各種不同的資料來源類型，包括 SQL Server、 Oracle、 Analysis Services、 XML 和 SQL Server Integration Services。 A**資料**索引標籤上，**版面配置**索引標籤上，並**預覽**索引標籤可讓您定義資料、 建立報表配置，以及預覽報表，全都放在相同的工作區。  
  
 您建立的控制項或報表伺服器的報表定義可以重複用於兩項技術。  
  
|若要建立報表伺服器執行的報表|  
|---|    
|1.在 **檔案**功能表上，選擇**新增**。<br />     [ **新增專案** ] 對話方塊隨即開啟。<br />2.在 **專案類型**窗格中，按一下**商業智慧專案**。<br />3.在 [範本] 窗格中，選取**報表伺服器專案**或是**報表伺服器專案精靈**。|  
  
## <a name="using-reportviewer-controls-and-sql-server-reporting-services-together"></a>使用 ReportViewer 控制項和 SQL Server Reporting Services 搭配  
 ReportViewer 控制項和 SQL Server 2005 Reporting Services 可以是中同時使用相同的應用程式。  
  
-   ReportViewer 控制項會提供用來在您的應用程式中顯示報表檢視器。  
  
-   Reporting Services 提供的報表，並在遠端伺服器上執行所有的處理。  
  
 ReportViewer 控制項可以設定為遠端的 Reporting Services 報表伺服器上顯示報表所儲存及處理。 這種設定稱為*遠端處理模式*。 在遠端處理模式中，控制會要求儲存在遠端報表伺服器的報表。 報表伺服器會執行所有的報表處理、 資料處理和轉譯報表。 完成後，轉譯的報表是傳回至控制項，並顯示在 [檢視] 區域中。  
  
 在其他報表伺服器支援執行的報表匯出格式，有不同的報表參數化實作，使用資料來源類型都受到報表伺服器，並經由上以角色為基礎的授權模型報表伺服器。  
  
 若要使用遠端處理模式中，指定的 URL 和路徑的伺服器報表設定 ReportViewer 控制項時。
