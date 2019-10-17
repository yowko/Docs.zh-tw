---
title: 基本程式設計週期
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320819"
---
# <a name="basic-programming-lifecycle"></a>基本程式設計週期
Windows Communication Foundation （WCF）可讓應用程式進行通訊，不論它們是在同一部電腦、跨網際網路或不同的應用程式平臺上。 本主題概述建立 WCF 應用程式所需的工作。 如需實用的範例應用程式，請參閱[消費者入門教學](getting-started-tutorial.md)課程。  
  
## <a name="the-basic-tasks"></a>基本工作  
 要執行的基本工作依序為：  
  
1. 定義服務合約。 服務合約可指定服務簽章、服務所交換的資料，以及其他合約所需的資料。 如需詳細資訊，請參閱[設計服務合約](designing-service-contracts.md)。  
  
2. 實作合約。 若要實作合約，請建立可實作合約的類別，然後指定執行階段應該具備的自訂行為。 如需詳細資訊，請參閱[執行服務合約](implementing-service-contracts.md)。  
  
3. 指定端點與其他行為資訊來設定服務。 如需詳細資訊，請參閱設定[服務](configuring-services.md)。  
  
4. 裝載服務。 如需詳細資訊，請參閱[裝載服務](hosting-services.md)。  
  
5. 建置用戶端應用程式。 如需詳細資訊，請參閱[建立用戶端](building-clients.md)。  
  
 儘管本章節的主題遵循此順序進行說明，在某些情況下並不會從第一個步驟開始。 例如，如果您想要為既有的服務建置用戶端，請從步驟 5 開始。 或者，如果您要建置其他人將使用的服務，則可以跳過步驟 5。  
  
 當您熟悉開發服務合約之後，您也可以閱讀擴充性[簡介](introduction-to-extensibility.md)。 如果您的服務有問題，請查看[WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)，以查看其他人是否有相同或類似的問題。  
  
## <a name="see-also"></a>請參閱

- [履行服務合約](implementing-service-contracts.md)
