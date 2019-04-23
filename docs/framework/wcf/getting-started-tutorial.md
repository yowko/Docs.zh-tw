---
title: 教學課程：開始使用 Windows Communication Foundation 應用程式
description: 這些教學課程提供建立 WCF 應用程式的簡介。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: d4613edefeb8db2c0d1e11e925f8ac41329efb0d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137919"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>教學課程：開始使用 Windows Communication Foundation 應用程式
下面一系列教學課程會為您介紹至 Windows Communication Foundation (WCF) 程式設計經驗。 透過這些教學課程中順序的工作會提供您建立 WCF 應用程式所需的步驟大致了解。 完成之後，您必須執行的 WCF 服務和 WCF 用戶端呼叫服務。 

此教學課程假設您使用 Visual Studio 作為開發環境。 如果您使用另一個開發環境，請略過 Visual Studio 特定指示。 

您可以下載並執行範例 WCF 應用程式，請參閱 < [Windows Communication Foundation 範例](samples/index.md)。 如需簡介範例，請參閱 <<c0> [ 開始使用範例](samples/getting-started-sample.md)。

如需建立服務和用戶端的詳細深入資訊，請參閱 <<c0> [ 基本 WCF 程式設計](basic-wcf-programming.md)。

## <a name="wcf-tutorials"></a>WCF 的教學課程

前三個教學課程說明如何定義 WCF 服務合約、 如何實作它，以及如何裝載它。 您所建立的服務是自我裝載的主控台應用程式中。 您也可以裝載在 Microsoft Internet Information Services (IIS 服務）。 如需詳細資訊，請參閱[如何：將 WCF 服務裝載於 IIS](feature-details/how-to-host-a-wcf-service-in-iis.md)。 雖然您可以使用程式碼來設定服務在本教學課程中，您也可以[設定服務組態檔內](configuring-services-using-configuration-files.md)。 

- [教學課程：定義服務合約](how-to-define-a-wcf-service-contract.md)

    您可以建立 WCF 合約具有使用者定義的介面。 此合約會定義服務所公開的功能。

- [教學課程：實作服務合約](how-to-implement-a-wcf-contract.md)

    定義合約之後，您必須透過服務類別來進行實作。

- [教學課程：裝載和執行基本的服務](how-to-host-and-run-a-basic-wcf-service.md)

    設定服務的端點，並將服務裝載於主控台應用程式。 服務才會變成作用中，您必須設定它，並裝載在執行階段環境中。 此執行階段環境中建立服務，並控制其內容和存留期。

下面兩個教學課程說明如何建立、 設定和使用用戶端應用程式，來呼叫服務作業公開 （expose）。 服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。 Visual Studio 會存取此中繼資料的程序自動化，並使用它來建構服務的用戶端應用程式。 如果您決定不使用 Visual Studio，您可以使用[ServiceModel Metadata Utility 工具 (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md)改。

- [教學課程：建立用戶端](how-to-create-a-wcf-client.md)

    擷取從 WCF 服務建立 WCF 用戶端 proxy 的中繼資料。 您使用 Visual Studio 加入服務參考來擷取中繼資料，或者您可以使用 ServiceModel Metadata Utility 工具。 您指定用戶端用來存取服務的端點。

- [教學課程：使用用戶端](how-to-use-a-wcf-client.md)

    您可以使用 WCF 用戶端 proxy 來呼叫服務作業。

## <a name="reference"></a>參考資料

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>另請參閱

- [概念式概觀](conceptual-overview.md)
- [文件指南](guide-to-the-documentation.md)
- [什麼是 Windows Communication Foundation](whats-wcf.md)
- [WCF 功能詳細資料](feature-details/index.md)
- [基本程式設計週期](basic-programming-lifecycle.md)
- [建置用戶端](building-clients.md)
- [基本 WCF 程式設計](basic-wcf-programming.md)
- [如何：建立雙工合約](feature-details/how-to-create-a-duplex-contract.md)
- [如何：Access services 搭配雙工合約](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel Metadata Utility 工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：使用 Svcutil.exe 來下載中繼資料文件](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [如何：發佈服務，使用組態檔的中繼資料](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [使用繫結設定服務和用戶端](using-bindings-to-configure-services-and-clients.md)
- [開始使用範例](samples/getting-started-sample.md)
- [Windows Communication Foundation 範例](samples/index.md)
- [自我裝載](samples/self-host.md)
