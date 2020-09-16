---
title: 支援的部署案例
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 299c8f2e29806a123e0a8b6e1e70d8cc13daa7bf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546246"
---
# <a name="supported-deployment-scenarios"></a>支援的部署案例

支援在部分信任應用程式中使用 Windows Communication Foundation (WCF) 功能的子集，是為了滿足使用 WCF 的部分（而非全部）案例的需求而設計。 在伺服器上，WCF 符合網際網路規模的共用主機服務提供者需求，這些提供者會基於安全性理由，在 ASP.NET 2.0 中信任許可權集合中執行協力廠商應用程式。 在用戶端上，WCF 部分信任支援的設計是為了滿足部署技術的需求，例如 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) 或 WPF 的 XAML 瀏覽器應用程式技術，可讓您從不受信任的網站進行無縫且安全的桌面應用程式部署。

## <a name="minimum-permission-requirements"></a>最低許可權需求

WCF 支援應用程式中，以下列其中一個標準命名許可權集合執行的功能子集：

- 中度信任權限

- 網際網路區域權限

在部分信任的應用程式中嘗試使用具有較嚴格許可權的 WCF，可能會在執行時間導致安全性例外狀況。

如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)。

## <a name="partial-trust-on-the-server"></a>伺服器上的部分信任

ASP.NET Web 應用程式裝載服務的許多商業提供者都要求在其伺服器上執行的應用程式會以 ASP.NET 2.0 中度信任許可權集合執行。 WCF 服務可以在這些環境中執行，前提是它們使用 <xref:System.ServiceModel.BasicHttpBinding> 、 <xref:System.ServiceModel.WebHttpBinding> 或搭配 <xref:System.ServiceModel.WSHttpBinding> 傳輸層級安全性。

在中度信任主機環境中執行的 WCF 服務，也可以藉由將訊息傳送至其他伺服器來回應用戶端要求，以作為中介層服務。 如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。

除了使用其中一個支援之 SOAP 系結的 SOAP 訊息之外，WCF 支援在 <xref:System.ServiceModel.WebHttpBinding> 部分信任的應用程式中建立 Web 樣式服務。 Wcf [WEB HTTP 程式設計模型](wcf-web-http-programming-model.md)、 [wcf 摘要整合](wcf-syndication.md)，以及 wcf 的 [AJAX 整合與 JSON 支援](ajax-integration-and-json-support.md) 功能全都在部分信任中受到支援。

工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。

如需詳細資訊，請參閱 [如何：在 ASP.NET 2.0 中使用中度信任](/previous-versions/msp-n-p/ff648344(v=pandp.10))。

## <a name="partial-trust-on-the-client"></a>用戶端上的部分信任

在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)和 WPF 的 XAML 瀏覽器應用程式 (XBAP) 技術都利用部分信任將有限的許可權授與不受信任的程式碼 (網際網路區域) 。

WCF 可以用來在 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) 或 XBAP 所部署的部分信任應用程式中，與遠端伺服器通訊。 網際網路區域許可權集合包含 <xref:System.Net.WebPermission> 來源主機的，可讓這些應用程式使用 [部分信任功能相容性](partial-trust-feature-compatibility.md)中所述的任何支援 WCF 系結來與其源伺服器通訊。

## <a name="see-also"></a>另請參閱

- [代碼啟用安全性](../../misc/code-access-security.md)
- [Windows Presentation Foundation 瀏覽器裝載的應用程式概觀](/dotnet/desktop/wpf/app-development/wpf-xaml-browser-applications-overview)
- [部分信任](partial-trust.md)
- [ASP.NET Trust Levels and Policy Files](/previous-versions/wyts434y(v=vs.140))
