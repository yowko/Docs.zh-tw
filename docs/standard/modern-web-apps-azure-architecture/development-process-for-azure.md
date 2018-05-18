---
title: Azure 開發程序
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | Azure 開發程序
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: 66f321d4671364fa1f7eebef98d53210098b5ed4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="development-process-for-azure"></a>Azure 開發程序

> _「借助雲端，個人和小型企業彈指之間就能立即設定企業級服務。」_  
> _- Roy Stephan_

 ## <a name="vision"></a>願景

> *以您喜歡的方式開發設計良好的 ASP.NET Core 應用程式，使用 Visual Studio 或 dotnet CLI 和 Visual Studio Code 或您選擇的編輯器。*

## <a name="development-environment-for-aspnet-core-apps"></a>ASP.NET Core 應用程式的開發環境

### <a name="development-tools-choices-ide-or-editor"></a>開發工具選擇：IDE 或編輯器

不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都能支援您開發 ASP.NET Core 應用程式。

**Visual Studio 2017.** 如果您使用 *Visual Studio 2017*，只要您已安裝「.NET Core 跨平台開發」工作負載，就可以建置 ASP.NET Core 應用程式。 圖 10-1 顯示 Visual Studio 2017 設定對話方塊中的必要工作負載。

![](./media/image10-1.png)

**圖 10-1.** 安裝 Visual Studio 2017 中的 .NET Core 工作負載。

[下載 Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code 和 dotnet CLI** (適用於 Mac、Linux 和 Windows 的跨平台工具)。 如果您偏好使用支援任何開發語言之輕量型且跨平台的編輯器，您可以使用 Microsoft Visual Studio Code 和 dotnet CLI。 這些產品提供簡單但強大的體驗，可簡化開發人員工作流程。 此外，Visual Studio Code 支援 C\# 及 Web 程式開發的延伸模組，並在編輯器中提供 Intellisense 和捷徑工作。

[下載 .NET Core SDK](https://www.microsoft.com/net/download/core)

[下載 Visual Studio Code](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Azure 裝載之 ASP.NET Core 應用程式的開發工作流程

應用程式開發生命週期從每位開發人員的電腦開始，開發人員使用其偏好的語言撰寫應用程式的程式碼，並在本機進行測試。 開發人員可以選擇偏好的原始檔控制系統，並且可使用組建伺服器或根據內建的 Azure 功能，設定持續整合 (CI) 及/或持續傳遞/部署 (CD)。

若要使用 CI/CD 開始開發 ASP.NET Core 應用程式，您可以使用 Visual Studio Team Services 或您組織自有的 Team Foundation Server (TFS)。

### <a name="initial-setup"></a>初始設定

若要建立應用程式的發行管線，您需要讓應用程式程式碼進入原始檔控制。 設定本機存放庫並在 Team 專案中將它連接至遠端存放庫。 請遵循下列指示：

-   [使用 Git 和 Visual Studio 共用程式碼](https://docs.microsoft.com/vsts/git/share-your-code-in-git-vs)或

-   [使用 TFVC 和 Visual Studio 共用程式碼](https://docs.microsoft.com/vsts/tfvc/share-your-code-in-tfvc-vs)

建立 Azure App Service，您將在其中部署應用程式。 前往 Azure 入口網站上的 [應用程式服務] 刀鋒視窗，建立 Web 應用程式。 按一下 [+新增]、選取 Web 應用程式範本、按一下 [建立]，然後提供名稱和其他詳細資料。 Web 應用程式將可從 {name}.azurewebsites.net 存取。

![AzureWebApp](./media/image10-2.png)

**圖 10-2.** 在 Azure 入口網站建立新的 Azure App Service Web 應用程式。

每當新的程式碼認可到專案的原始檔控制存放庫時，CI 的建置程序將會執行自動化建置。 這可提供您程式碼建置 (以及在理想的情況下，通過自動化測試) 且可能部署的立即回應。 這個 CI 組建將會產生 Web 部署套件成品，並發佈它以供您的 CD 程序取用。

[定義 CI 組建流程](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#ci)

請務必啟用持續整合，以便每當您小組中有人認可新的程式碼時，系統便將建置排入佇列中。 測試組建，並確認它產生 Web 部署套件作為其中一個成品。

建置成功時，您的 CD 程序會將 CI 組建的結果部署至 Azure Web 應用程式。 若要設定這種情況，您需要建立及設定「發行」，這會部署到您的 Azure App Service。

[定義 CD 發行程序](https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core#cd)

CI/CD 管線設定之後，您就可以直接更新 Web 應用程式，並認可到原始檔控制中以便部署。

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Azure 裝載之 ASP.NET Core 應用程式的開發工作流程

一旦您設定好 Azure 帳戶和 CI/CD 程序，開發 Azure 裝載的 ASP.NET Core 應用程式便很簡單。 以下是建置 ASP.NET Core 應用程式 (裝載於 Azure App Service 中作為 Web 應用程式) 時通常會採取的基本步驟，如圖 10-3 所示。

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**圖 10-3.** 建置 ASP.NET Core 應用程式並將其裝載在 Azure 中的逐步工作流程

#### <a name="step-1-local-dev-environment-inner-loop"></a>步驟 1： 本機開發環境內部迴圈

開發您的 ASP.NET Core 應用程式以便部署至 Azure，與用其他方式開發應用程式並無不同。 使用您慣用的本機開發環境，不論是 Visual Studio 2017 或 dotnet CLI 和 Visual Studio Code 或您偏好的編輯器。 您可以撰寫程式碼、執行變更並加以偵錯、執行自動化測試，以及本機認可至原始檔控制，直到您準備好要將變更推送到共用原始檔控制存放庫。

#### <a name="step-2-application-code-repository"></a>步驟 2： 應用程式程式碼存放庫

當您準備好要與小組共用程式碼時，您應該從您的本機來源存放庫推送變更至小組的共用原始程式碼存放庫。 如果您已在自訂的分支中工作，這個步驟通常牽涉到將您的程式碼合併到共用的分支 (可能是透過[提取要求](https://docs.microsoft.com/vsts/git/pull-requests)的方式)。

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>步驟 3： 組建伺服器：持續整合。 建置、測試、封裝

每當對共用應用程式程式碼存放庫進行新的認可時，便會在組建伺服器上觸發新的建置。 在 CI 程序中，這項建置應該完整編譯應用程式，並執行自動化的測試，以確認一切如預期般運作。 CI 程序的最終結果應為 Web 應用程式的封裝版本，準備好進行部署。

#### <a name="step-4-build-server-continuous-delivery"></a>步驟 4： 組建伺服器：持續傳遞

建置成功之後，CD 程序會取得所產生的組建成品。 這會包括 Web 部署套件。 組建伺服器會將此套件部署至 Azure App Service，以新建的服務來取代任何現有的服務。 此步驟通常以預備環境為目標，但某些應用程式會透過 CD 程序直接部署至生產環境。

#### <a name="step-5-azure-app-service-web-app"></a>步驟 5： Azure App Service。 Web 應用程式。

部署之後，ASP.NET Core 應用程式會在 Azure App Service Web 應用程式的內容裡執行。 可以使用 Azure 入口網站來監視及進一步設定此 Web 應用程式。

#### <a name="step-6-production-monitoring-and-diagnostics"></a>步驟 6： 生產環境監視及診斷

Web 應用程式在執行時，您可以監視應用程式的健康狀態，並收集診斷和使用者行為資料。 Application Insights 隨附於 Visual Studio 中，並提供 ASP.NET 應用程式的自動檢測。 它可以提供您使用方式、例外狀況、要求、效能和記錄檔的相關資訊。

## <a name="references"></a>參考

**建置並部署 ASP.NET Core 應用程式至 Azure**  
<https://docs.microsoft.com/vsts/build-release/apps/aspnet/build-aspnet-core>


>[!div class="step-by-step"]
[上一頁] (test-asp-net-core-mvc-apps.md) [下一頁] (azure-hosting-recommendations-for-asp-net-web-apps.md)
