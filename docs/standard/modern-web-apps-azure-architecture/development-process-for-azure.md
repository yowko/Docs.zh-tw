---
title: "Azure 的開發程序"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |Azure 的開發程序"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: e676c1225f7d11381808040cf101e897e0726ad4
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="development-process-for-azure"></a>Azure 的開發程序

> _「 雲端，個人或小型企業可以貼齊其指並立即設定企業級服務 」 的。_  
> _-伊 Stephan_

 ## <a name="vision"></a>Vision

> *開發設計良好的 ASP.NET Core 應用程式的方式，使用 Visual Studio 或 dotnet CLI，Visual Studio 程式碼或您選擇的編輯器。*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core 應用程式的開發環境

### <a name="development-tools-choices-ide-or-editor"></a>開發工具的選擇： IDE 或編輯器

是否完整且功能強大的 IDE 或套輕量型且敏捷式軟體開發編輯器想，Microsoft 會具有您涵蓋開發 ASP.NET Core 應用程式時。

**Visual Studio 2017。** 如果您使用*Visual Studio 2017* ASP.NET Core 應用程式，只要您有*.NET Core 跨平台開發*安裝的工作負載。 圖 10-1 會顯示在 Visual Studio 2017 的 [設定] 對話方塊所需的工作負載。

![](./media/image10-1.png)

**圖 10-1。** 在 Visual Studio 2017 安裝.NET Core 工作負載。

[下載 Visual Studio 2017](https://www.visualstudio.com/downloads/)

**Visual Studio 程式碼和 dotnet CLI** （適用於 Mac、 Linux 和 Windows 的跨平台工具）。 如果您想支援任何開發語言的輕量型和跨平台編輯器，您可以使用 Microsoft Visual Studio 程式碼及 dotnet CLI。 這些產品提供簡化的開發人員工作流程的簡單但強大體驗。 此外，Visual Studio 程式碼支援擴充功能的 C\#及 web 程式開發，提供 intellisense 和快顯的工作，在編輯器中。

[下載.NET Core SDK](https://www.microsoft.com/net/download/core)

[下載 Visual Studio 程式碼](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure 裝載的 ASP.NET Core 應用程式的開發工作流程

從每個開發人員的電腦，撰寫程式碼應用程式使用其偏好的語言，以及在本機測試它，啟動應用程式開發週期。 開發人員可以選擇其慣用的原始檔控制系統和持續整合 (CI) 及/或連續傳遞/部署 (CD) 使用的組建伺服器可以設定或根據內建的 Azure 功能。

若要開始開發使用 CI/CD 的 ASP.NET Core 應用程式，您可以使用 Visual Studio Team Services 或您的組織擁有 Team Foundation Server (TFS)。

### <a name="initial-setup"></a>初始安裝

若要建立您的應用程式的發行管線，您需要有原始檔控制中的應用程式程式碼。 設定本機儲存機制並將它連接至 team 專案中的遠端儲存機制。 遵循下列指示：

-   [Visual Studio 與 Git 共用程式碼](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs)或

-   [與 TFVC 和 Visual Studio 共用程式碼](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

建立 Azure 應用程式服務，您要在其中部署應用程式。 建立 Web 應用程式，請前往 Azure 入口網站上的 [應用程式服務] 刀鋒視窗。 按一下 [+ 新增]，選取的 Web 應用程式範本、 按一下 [建立] 並提供名稱和其他詳細資料。 Web 應用程式仍可從 {name}。 名稱是.azurewebsites.net。

![AzureWebApp](./media/image10-2.png)

**圖 10-2。** 在 Azure 入口網站建立新 Azure App Service Web 應用程式。

CI 的建置程序將會執行自動化的組建，每當新的程式碼致力於專案的原始檔控制儲存機制。 這可讓您建置程式碼的立即回應 （甚至是理想的情況下，會將自動化的測試的傳遞），而且可能部署。 這個 CI 組建將會產生 web 部署封裝成品並發佈它供您的 CD 程序。

[定義 CI 建置流程](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

請務必啟用連續整合，因此系統將組建排入佇列中的某個人您的小組認可新的程式碼時。 測試建置，並確認它產生 web 部署套件做為其中一個及其成品。

建置成功時，您的 CD 程序會加入至 Azure web 應用程式部署 CI 組建的結果。 若要設定這種情況，您需要建立及設定*發行*，這會將部署到您的 Azure 應用程式服務。

[定義您的 CD 發行流程](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

CI/CD 管線設定之後，您就可以只讓 web 應用程式的更新，並將它們部署的原始檔控制中認可這些。

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>開發 Azure 裝載的 ASP.NET Core 應用程式的工作流程

一旦您已設定您的 Azure 帳戶和您 CI/CD 的程序，開發 Azure 裝載的 ASP.NET Core 應用程式很簡單。 以下是您通常會採用建置的說明圖 10-3 做為 Web 應用程式中，裝載在 Azure App Service 中的 ASP.NET Core 應用程式時的基本步驟。

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**圖 10-3。** 逐步建立 ASP.NET Core 應用程式和其裝載在 Azure 中的工作流程

#### <a name="step-1-local-dev-environment-inner-loop"></a>步驟 1： 本機開發環境內部迴圈

開發您的 ASP.NET Core 應用程式部署至 Azure 並無不同否則開發應用程式。 使用本機開發環境，您已經熟悉，不論是 Visual Studio 2017 或 dotnet CLI，Visual Studio 程式碼或您慣用的編輯器。 您可以撰寫程式碼、 執行和偵錯您的變更、 執行自動化的測試，及至原始檔控制，直到您準備好要將變更推送到您的共用原始檔控制儲存機制進行本機認可。

#### <a name="step-2-application-code-repository"></a>步驟 2： 應用程式程式碼儲存機制

當您準備好要與小組共用您的程式碼時，您應該從您的本機來源儲存機制推送變更至您的小組共用的原始程式碼儲存機制。 如果您已在自訂的分支中，這個步驟通常包含您的程式碼合併到共用的分支 (可能是透過的方式[提取要求](https://www.visualstudio.com/docs/git/pull-requests))。

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>步驟 3： 持續整合組建伺服器:。 建置、 測試套件

只要新的認可對共用的應用程式程式碼儲存機制在組建伺服器上觸發新組建。 CI 程序的一部分，此組建應該完全編譯應用程式，並執行自動化的測試，以確認一切如預期般運作。 CI 程序的最終結果應為 web 應用程式，準備好進行部署的封裝的版本。

#### <a name="step-4-build-server-continuous-delivery"></a>步驟 4： 組建伺服器： 持續傳遞

一次建置成功時，在 CD 程序將挑選所產生的組建成品。 這包括 web 部署套件。 組建伺服器會將此封裝部署至 Azure App Service，以新建一個取代任何現有的服務。 此步驟通常為目標預備環境，但某些應用程式直接部署至實際執行透過 CD 的程序。

#### <a name="step-5-azure-app-service-web-app"></a>步驟 5： Azure App Service。 Web 應用程式。

一旦部署之後，ASP.NET Core 應用程式會執行在 Azure App Service Web 應用程式的內容。 此 Web 應用程式可以監視，並進一步設定使用 Azure 入口網站。

#### <a name="step-6-production-monitoring-and-diagnostics"></a>步驟 6： 實際執行監視和診斷

執行 Web 應用程式時，您可以監視應用程式的健全狀況和收集診斷和使用者行為資料。 Application Insights 隨附於 Visual Studio 中，並提供 ASP.NET 應用程式的自動檢測。 它可以提供您使用量、 例外狀況、 要求、 效能和記錄檔的相關資訊。

## <a name="references"></a>參考

**建置和部署您的 ASP.NET Core 應用程式至 Azure**  
<https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure>


>[!div class="step-by-step"]
[上一個](test-asp-net-core-mvc-apps.md) [下一步] (azure-hosting-recommendations-for-asp-net-web-apps.md)
