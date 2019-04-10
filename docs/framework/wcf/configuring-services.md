---
title: 設定 WCF 服務
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: 81727adbf985986a71cc9f9e2d42a1de0cb1fd76
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156503"
---
# <a name="configuring-wcf-services"></a>設定 WCF 服務

在設計並實作您的服務合約之後，就可開始設定您的服務。 您可在此處定義及自訂向用戶端公開服務的方式，包括指定所在的位址、用於傳送及接收訊息的傳輸和訊息編碼，以及所需要的安全性類型。  
  
 此處所使用的組態包括所有的方法，如命令式程式碼或使用組態檔，您可以在其中定義及自訂服務的各方面，例如指定端點位址、使用的傳輸以及安全性配置。 在實務上，撰寫組態是主要的程式設計 WCF 應用程式一部分。  
  
## <a name="in-this-section"></a>本節內容  
 [簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)  
 從開始[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]，WCF 本身就有新的預設組態模型，可簡化 WCF 組態需求。 如果您未提供任何特定服務的 WCF 組態，執行階段會使用預設端點、 繫結和行為自動設定您的服務。  
  
 [使用組態檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Windows Communication Foundation (WCF) 服務是可設定使用[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]技術設定。 大多數情況下，XML 項目會新增至裝載的 WCF 服務的 Internet Information Services (IIS) 網站的 Web.config 檔案。 這些項目允許您變更詳細資料，例如各電腦的端點位址 (用於與服務通訊的實際位址)。  
  
 [繫結](../../../docs/framework/wcf/bindings.md)  
 此外，WCF 會包含數個系統提供的常用組態的繫結可讓您快速選取用戶端與服務通訊的方式，例如傳輸、 安全性和訊息編碼使用的最基本的功能形式。  
  
 [端點](../../../docs/framework/wcf/endpoints.md)  
 使用 WCF 服務的所有通訊都都會透過*端點*的服務。 端點包含合約、在繫結中指定的組態資訊，以及指出何處可找到服務或何處可取得有關服務之資訊的位址。  
  
 [保護服務的安全](../../../docs/framework/wcf/securing-services.md)  
 使用 WCF，與現有安全性機制，您可以實作機密性、 完整性、 驗證和授權，在任何服務。 您也可以稽核安全性成功和失敗。  
  
 [建立 WS-I Basic Profile 1.1 互通服務](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 在 WS-I Basic Profile 1.1 規格中略述了部署與其他平台或作業系統上的服務和用戶端互通之服務的需求。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>相關章節  
 [基本程式設計週期](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [裝載服務](../../../docs/framework/wcf/hosting-services.md)  
  
 [建置用戶端](../../../docs/framework/wcf/building-clients.md)  
  
 [擴充性簡介](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>另請參閱

- [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)
- [概觀說明](../../../docs/framework/wcf/conceptual-overview.md)
- [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)
