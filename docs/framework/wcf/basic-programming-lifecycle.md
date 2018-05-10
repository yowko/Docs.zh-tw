---
title: 基本程式設計週期
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: b20167ad776f3524e4516b71e43ab8cdb5c2aea4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="basic-programming-lifecycle"></a>基本程式設計週期
Windows Communication Foundation (WCF) 可讓它們是否在相同的電腦上透過網際網路，或在不同的應用程式平台上進行通訊的應用程式。 本主題概要說明建置的 WCF 應用程式所需的工作。 可用的範例應用程式，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)。  
  
## <a name="the-basic-tasks"></a>基本工作  
 要執行的基本工作依序為：  
  
1.  定義服務合約。 服務合約可指定服務簽章、服務所交換的資料，以及其他合約所需的資料。 如需詳細資訊，請參閱[設計服務合約](../../../docs/framework/wcf/designing-service-contracts.md)。  
  
2.  實作合約。 若要實作合約，請建立可實作合約的類別，然後指定執行階段應該具備的自訂行為。 如需詳細資訊，請參閱[實作服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)。  
  
3.  指定端點與其他行為資訊來設定服務。 如需詳細資訊，請參閱[設定 Services](../../../docs/framework/wcf/configuring-services.md)。  
  
4.  裝載服務。 如需詳細資訊，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。  
  
5.  建置用戶端應用程式。 如需詳細資訊，請參閱[建置用戶端](../../../docs/framework/wcf/building-clients.md)。  
  
 儘管本章節的主題遵循此順序進行說明，在某些情況下並不會從第一個步驟開始。 例如，如果您想要為既有的服務建置用戶端，請從步驟 5 開始。 或者，如果您要建置其他人將使用的服務，則可以跳過步驟 5。  
  
 一旦您熟悉開發服務合約時，您也可以讀取[擴充性簡介](../../../docs/framework/wcf/introduction-to-extensibility.md)。 如果您有與服務的問題，請檢查[WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)若要查看其他人是否具有相同或類似的問題。  
  
## <a name="see-also"></a>另請參閱  
 [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)
