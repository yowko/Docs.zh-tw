---
title: 選擇正確的 Azure 裝載選項
description: 了解哪些 Azure 移轉路徑適合您的 ASP.NET Web 應用程式。
author: CESARDELATORRE
ms.author: cesardl
ms.date: 03/01/2020
ms.openlocfilehash: a8ad946b03f97272cb8685620858af6b21a372dc
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "82072106"
---
# <a name="choose-the-right-azure-hosting-option"></a>選擇正確的 Azure 裝載選項

本文提供 Azure 中從本地遷移到 Azure 的現有 .NET 框架應用程式時有多個選項之間的注意事項和比較。

將現有 .NET 應用程式移轉至 Azure 時要考慮的基本領域如下︰

1. 計算服務選項
1. 資料庫選項
1. 網路和安全性考量
1. 驗證和授權考量

## <a name="compute-choices"></a>計算服務選項

將現有的 .NET Framework 應用程式移轉至 Azure 時則會有多個選項。 不過，因為 .NET Framework 相依於 Windows，下列選項僅限於以 Windows 為基礎的計算服務。

下表列出數個比較和建議，可協助您為現有的 .NET 應用程式選擇適合的計算移轉路徑。

|                 | Azure VM | Azure App Service | Windows 容器 |
|-----------------|-----------|-------------------|--------------------|
|使用時機      |<ul><li>應用程式在伺服器和本機 .msi 安裝上具有強烈相依性。</li><li>您會希望應用程式移轉路徑越簡單越好</li></ul>|應用程式與伺服器沒有相依性，是個乾淨的 ASP.NET Web 應用程式 (MVC、WebForm) 或存取資料庫伺服器的多層式架構應用程式 (Web API、WCf)。 |<ul><li>應用程式在原始伺服器上具有相依性，但這些相依性可以包含在 Docker Windows 映像中。</li><li>想要使應用程式現代化,以便實現[雲開發人員準備](../../architecture/modernize-with-azure-containers/modernize-existing-apps-to-cloud-optimized/reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications.md)</li></ul>|
|優點與好處  |<ul><li>最簡單的移轉路徑</li><li>熟悉的環境。 部署環境是 VM,因此類似於本地伺服器。</li></ul> |進行中的 PaaS 維護作業是在 Azure 中管理和調整應用程式最簡單的方式。 |<ul><li>雲開發人員準備與應用容器中包含的依賴項。</li><li>幾乎不需要重構 .NET /C# 代碼。</li></ul> |
|缺點             |此為 IaaS。 維護成本昂貴。 您必須管理 VM 有關網路、負載均衡器、橫向擴展、IIS 管理等的基礎結構。 |<ul><li>並未[支援](https://appmigration.microsoft.com/assessment)所有的應用程式</li><li>某些應用可能需要重構,甚至稍微重新構建,以便它們支援 Azure 應用服務。</li></ul> |<ul><li>Docker 的技能學習曲線</li><li>某些程式碼和應用程式組態設定會變更</li></ul>|
|需求 |比起內部部署應用程式，具有相同需求的 Windows Server VM | 在[就緒檢查](https://github.com/Azure/App-Service-Migration-Assistant/wiki/Readiness-Checks)中指定的 Azure 應用服務要求。 |<ul><li>[Docker 引擎 - 適用於 Windows 伺服器的 2019](https://azuremarketplace.microsoft.com/marketplace/apps/cloud-infrastructure-services.docker-windows-2019)<br />或</li><li>[Azure Container Service (AKS)](https://azure.microsoft.com/services/container-service/) (此為 Kubernetes 協調器)<br />或<li>[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) 協調器</li></ul> |
|如何移轉 |請參閱[移轉至 Azure 虛擬機器](vm.md) | 請參閱[移轉 Azure App Service](app-service.md) | 遵循[Azure 和 Windows 容器電子書實現現有 .NET 應用的現代化](https://aka.ms/liftandshiftwithcontainersebook)中解釋的注意事項、方案和演練 |

以程式圖圖顯示了規劃現有 . NET Framework 應用程式遷移到 Azure 時的決策樹。 如果可行,請嘗試首先選擇選項 A,但選項 B 是最容易執行的路徑。

![顯示裝載決策樹的流程圖](../media/migration/choose/decision-tree.png)

## <a name="database-choices"></a>資料庫選項

將關聯式資料庫移轉到 Azure 時您有多個選項。 請參閱[將 SQL Server 資料庫移轉至 Azure](sql.md)，可協助您為現有的 .NET 應用程式選擇正確的資料庫移轉路徑。

## <a name="networking-and-security-considerations"></a>網路和安全性考量

在將應用程式部署至如 Microsoft Azure 等公用雲端時，您可能想要[建立網路 DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/) 來隔離和保護特定網路，例如 [Azure 與內部部署間的周邊網路](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-hybrid) 或 [Azure 與網際網路間的 DMZ](https://docs.microsoft.com/azure/architecture/reference-architectures/dmz/secure-vnet-dmz)。 周邊網路可以透過 [Azure 虛擬網路](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)來實作。

Azure 虛擬網路可讓您：

- 建置可控制的混合式基礎結構
- 使用自己的 IP 位址與 DNS 伺服器
- 利用 IPsec VPN 或 ExpressRoute 保障連線的安全
- 對子網路間的流量進行細微的控制
- 使用虛擬應用設備建立精密的網路拓撲
- 為您的應用程式提供一個孤立且高度安全的環境

若要開始建置您自己的虛擬網路，請參閱 [Azure 虛擬網路文件](https://docs.microsoft.com/azure/virtual-network/)。

## <a name="authentication-and-authorization-considerations-when-migrating-to-azure"></a>移轉至 Azure 時的驗證和授權考量

任何組織要移到雲端時的首要考量皆是安全性。 大多數公司都投入了大量的時間、資金和工程來設計和開發安全模型,因此,能夠利用現有投資(如標識存儲和單一登錄解決方案)非常重要。

許多執行於內部部署的現有企業 B2E .NET 應用程式使用 Active Directory 進行驗證和身分識別管理。 Azure AD Connect 可讓您整合內部部署目錄與 Azure Active Directory。 若要開始，請參閱[整合您的內部部署目錄與 Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。

請參閱[混合式身分識別解決方案的身分識別需求](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-business-needs)以進一步進行 Azure Active Directory 的相關規劃。

其他驗證通訊協定的選擇還有 [OAuth](https://en.wikipedia.org/wiki/OAuth) 和 [OpenID](https://en.wikipedia.org/wiki/OpenID)，其在消費者導向應用程式中很常見。 使用自發的身分識別資料庫 (例如由 IdentityServer4 使用 OAuth 包裝的 ASP.NET 身分識別 SQL 資料庫)，通常不需連線到內部部署資料庫或目錄。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [將ASP.NET Web 應用程式移轉到 Azure 應用服務](app-service.md)
