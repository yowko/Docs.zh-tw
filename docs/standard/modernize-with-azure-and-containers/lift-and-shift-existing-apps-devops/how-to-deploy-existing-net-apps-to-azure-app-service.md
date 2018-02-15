---
title: "如何將現有的.NET 應用程式部署至 Azure App Service"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |如何將現有的.NET 應用程式部署至 Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84bffe7aad6bbffb40519c9146d8156159d55850
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>如何將現有的.NET 應用程式部署至 Azure App Service 

Azure App Service Web 應用程式功能是完全受管理的運算平台，並針對主控網站和 web 應用程式最佳化。 此 PaaS 供應項目，在 Microsoft Azure 可讓您專注於商務邏輯，而 Azure 會負責執行，並調整您的應用程式的基礎結構。

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>驗證站台，並移轉至 App Service 與 Azure 應用程式服務移轉小幫手

當您建立新的應用程式在 Visual Studio 中，將應用程式移至應用程式服務通常相當簡單。 不過，如果您正在規劃移轉現有應用程式服務的應用程式，您必須先評估所有應用程式的相依性是否與應用程式服務相容。 這包括伺服器作業系統和伺服器安裝任何協力廠商軟體相依性。

您可以使用[Azure 應用程式服務移轉小幫手](https://www.migratetoazure.net/)來分析網站並再將它們從 Windows 和 Linux 的 web 伺服器，移轉到應用程式服務。 移轉的一部分，此工具會建立 web 應用程式，且資料庫在 Azure 上的如有需要發行的內容，並發行您的資料庫。

Azure 應用程式服務移轉小幫手支援移轉至雲端的 Windows Server 上執行的 iis。 應用程式服務支援 Windows Server 2003 和更新版本。

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> **圖 4-5。** 使用 Azure App Service 移轉小幫手

應用程式服務移轉小幫手是一種工具，將您的網站，從您網頁伺服器移至 Azure 雲端。

網站移轉至 App Service 之後，站台會有安全而有效率地執行所需要的所有項目。 站台所設定，並自動在 Azure 雲端 PaaS 服務 （應用程式服務） 中執行。

應用程式服務移轉工具可以分析您的網站，並報告其相容性移至應用程式服務。 如果您很滿意分析，您可以讓應用程式服務移轉小幫手移轉內容、 資料和設定。 如果網站不完全相容，則會移轉工具，告訴您需要調整，以讓它運作。

### <a name="additional-resources"></a>其他資源

-   **Azure App Service 移轉小幫手**

    [https://www.migratetoazure.net/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[上一頁](what-about-cloud-optimized-applications.md)
[下一頁](deploy-existing-net-apps-as-windows-containers.md)
