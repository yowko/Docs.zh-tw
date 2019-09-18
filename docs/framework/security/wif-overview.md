---
title: Windows Identity Foundation 4.5 概觀
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: c9420ce641da32edc6196be0743d967446a14947
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044998"
---
# <a name="windows-identity-foundation-45-overview"></a>Windows Identity Foundation 4.5 概觀
Windows Identity Foundation 4.5 是一組 .NET Framework 類別，可在應用程式中用來實作宣告型識別。 透過它，您可以更容易享受到宣告感知應用程式和服務的優點。 只要是使用 .NET Framework 4.5 (含) 以上版本的所有 Web 應用程式或 Web 服務，WIF 4.5 都適用。 WIF 只是 Microsoft 同盟識別身分軟體系列的一部分，可以根據開放標準達成業界共同的願景。 同盟身分識別包含三個元件：[Active Directory®同盟服務](https://go.microsoft.com/fwlink/?LinkID=247516)（AD FS）2.0、 [Windows Azure 存取控制 Services](https://go.microsoft.com/fwlink/?LinkID=247517) （ACS）和 WIF。 這三個元件同時也形成了 Microsoft 新的宣告型雲端識別和存取平台的核心。  
  
 如需 WIF 的詳細資訊，請參閱 MSDN 上安全性開發人員中心的[Windows Identity Foundation 網站](https://go.microsoft.com/fwlink/?LinkId=149009)。 如需使用 WIF 建立應用程式的簡介，請參閱[Windows Identity Foundation](https://www.microsoftpressstore.com/store/programming-windows-identity-foundation-9780735627185) By Vittorio Bertocci 的程式設計（由 Microsoft 按下發布）。  
  
## <a name="wif-45-features"></a>WIF 4.5 的功能  
 WIF 4.5 是用於建置識別感知應用程式的架構。 這個架構擷取 WS-Trust 和 WS-Federation 通訊協定，方便開發人員利用 API 建置宣告感知應用程式並視需要建置 Security Token Service (STS)。 應用程式可以使用 WIF 處理 STS (例如 AD FS 2.0 和 ACS) 發行的權杖，並在 Web 應用程式或 Web 服務制定識別架構決策。  
  
 WIF 4.5 具有下列主要功能：  
  
- 建置宣告感知應用程式 (信賴憑證者應用程式)： WIF 可協助開發人員建置宣告感知應用程式。 除了提供宣告模型以外，它還提供應用程式開發人員一組豐富的 API，協助根據宣告制定使用者存取決策。  此外，無論開發人員選擇在 ASP.NET 還是 WCF 環境中建置應用程式，WIF 都能提供一致的程式設計經驗。  
  
- 將識別委派支援加入至宣告感知應用程式：  WIF 可跨多個服務界限保留原始要求者的識別。 這項功能可以透過架構中的 "ActAs" 或 "OnBehalfOf" 功能達成，讓開發人員能夠在宣告感知應用程式中加入識別委派支援。  
  
- 建置自訂 STS：  使用 WIF 可讓開發人員更容易建置支援 WS-Trust 通訊協定的自訂 STS。 這類 STS 也稱為主動式 STS。  
  
     此外，這個架構還可用來建置支援 WS-Federation 的 STS，讓 Web 瀏覽器用戶端也可以使用。 這類 STS 也稱為被動式 STS。  
  
- 適用於 Visual Studio 11 的新識別和存取工具可讓您透過宣告型識別確保應用程式安全無虞，並且能接受使用者來自多個識別提供者。 您可以從下列 URL 下載此 WIF 工具： <https://go.microsoft.com/fwlink/?LinkID=245849>或直接在 [延伸模組管理員] 中搜尋「身分識別」，從 Visual Studio 11 開始。 如需詳細資訊，請參閱 [Visual Studio 2012 的身分識別與存取工具](identity-and-access-tool-for-vs.md)。  
  
 WIF 支援下列主要案例：  
  
- 同盟：  WIF 可讓兩個或多個合作夥伴建立同盟。 它支援建置宣告感知應用程式 (RP) 和自訂 STS，可協助開發人員落實此案例。  
  
- 識別委派：  WIF 讓跨服務界限保留識別更為容易，方便開發人員落實識別委派案例。  
  
- 加強驗證： 應用程式中不同資源的驗證需求可能都不同。 WIF 可讓開發人員建置能要求累加式驗證需求的應用程式 (例如，透過使用者名稱/密碼驗證進行初次登入，接著使用智慧卡來加強驗證)。  
  
 使用 WIF，您可以更容易享受到宣告型識別模型的優點。 如需詳細資訊，請參閱[適用於開發人員的 Windows Identity Foundation 白皮書](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf)。
