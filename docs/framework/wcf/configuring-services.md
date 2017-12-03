---
title: "設定服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de970bf27fdf3365daa0ac515852a68d01a246eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-services"></a>設定服務
在設計並實作您的服務合約之後，就可開始設定您的服務。 您可在此處定義及自訂向用戶端公開服務的方式，包括指定所在的位址、用於傳送及接收訊息的傳輸和訊息編碼，以及所需要的安全性類型。  
  
 此處所使用的組態包括所有的方法，如命令式程式碼或使用組態檔，您可以在其中定義及自訂服務的各方面，例如指定端點位址、使用的傳輸以及安全性配置。 事實上，撰寫組態是程式設計 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式的主要部分。  
  
## <a name="in-this-section"></a>本章節內容  
 [簡化設定](../../../docs/framework/wcf/simplified-configuration.md)  
 從 [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]開始， [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 隨附可簡化 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 組態需求的新預設組態模型。 如果您沒有對特定服務提供任何 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 組態，執行階段會以預設端點、繫結和行為自動設定服務。  
  
 [使用設定檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務可使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 組態技術來設定。 最常見的是，會將 XML 項目新增至裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的網際網路資訊服務 (IIS) 網站的 Web.config 檔案。 這些項目允許您變更詳細資料，例如各電腦的端點位址 (用於與服務通訊的實際位址)。  
  
 [繫結](../../../docs/framework/wcf/bindings.md)  
 此外，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 還包括數種系統提供的常用組態，並以繫結的形式表示，允許您快速選取用戶端和服務如何通訊的最基本功能，例如所使用的傳輸、安全性和訊息編碼。  
  
 [端點](../../../docs/framework/wcf/endpoints.md)  
 所有與通訊[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]服務會透過*端點*的服務。 端點包含合約、在繫結中指定的組態資訊，以及指出何處可找到服務或何處可取得有關服務之資訊的位址。  
  
 [保護服務安全](../../../docs/framework/wcf/securing-services.md)  
 使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 和現有的安全性機制，您可以在任何服務中實作機密性、完整性、驗證和授權。 您也可以稽核安全性成功和失敗。  
  
 [建立 WS-I Basic Profile 1.1 交互操作服務](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
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
 [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [概念性概觀](../../../docs/framework/wcf/conceptual-overview.md)  
 [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)
