---
title: 教學課程：開始使用 Windows Communication Foundation 應用程式
description: 這些教學課程提供建立 WCF 應用程式的簡介。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 620a83260f01e27a19b19227165695a621c88e5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238232"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>教學課程：開始使用 Windows Communication Foundation 應用程式

下列一系列的教學課程將為您介紹 Windows Communication Foundation (WCF) 程式設計體驗。 依序執行這些教學課程可讓您瞭解建立 WCF 應用程式所需的步驟。 完成之後，您將會有執行中的 WCF 服務和呼叫服務的 WCF 用戶端。

本教學課程假設您使用 Visual Studio 作為開發環境。 如果您使用的是其他開發環境，請忽略 Visual Studio 特定的指示。

如需可供下載並執行的 WCF 應用程式範例，請參閱 [Windows Communication Foundation 範例](samples/index.md)。 如需範例的簡介，請參閱使用者 [入門範例](samples/getting-started-sample.md)。

如需有關建立服務和用戶端的更深入資訊，請參閱 [基本 WCF 程式設計](basic-wcf-programming.md)。

## <a name="wcf-tutorials"></a>WCF 教學課程

前三個教學課程將說明如何定義 WCF 服務合約、如何執行它，以及如何裝載它。 您所建立的服務會在主控台應用程式中自我裝載。 您也可以在 Microsoft Internet Information Services (IIS) 上裝載服務。 如需詳細資訊，請參閱 [如何：在 IIS 中裝載 WCF 服務](feature-details/how-to-host-a-wcf-service-in-iis.md)。 雖然您在教學課程中使用程式碼來設定服務，但是您也可以在 [設定檔中設定服務](configuring-services-using-configuration-files.md)。

- [教學課程：定義服務合約](how-to-define-a-wcf-service-contract.md)

    您可以使用使用者定義的介面來建立 WCF 合約。 此合約會定義服務所公開的功能。

- [教學課程：執行服務合約](how-to-implement-a-wcf-contract.md)

    定義合約之後，您必須使用服務類別來執行它。

- [教學課程：裝載和執行基本服務](how-to-host-and-run-a-basic-wcf-service.md)

    設定服務的端點，並在主控台應用程式中裝載服務。 若要讓服務成為使用中，您必須在執行時間環境內進行設定，並將其裝載在執行時間環境中。 此執行時間環境會建立服務並控制其內容和存留期。

接下來的兩個教學課程將說明如何建立、設定及使用用戶端應用程式，以呼叫服務所公開的作業。 服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。 Visual Studio 會將存取此中繼資料的程式自動化，並使用它來建立服務的用戶端應用程式。 如果您決定不使用 Visual Studio，可以改為使用 [ [System.servicemodel 中繼資料公用程式] 工具 (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) 。

- [教學課程：建立用戶端](how-to-create-a-wcf-client.md)

    從 WCF 服務取出用來建立 WCF 用戶端 proxy 的中繼資料。 您可以使用 Visual Studio 來取得中繼資料來新增服務參考，也可以使用 [System.servicemodel 中繼資料公用程式] 工具。 您可以指定用戶端用來存取服務的端點。

- [教學課程：使用用戶端](how-to-use-a-wcf-client.md)

    使用 WCF 用戶端 proxy 呼叫服務作業。

## <a name="reference"></a>參考

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>另請參閱

- [概念總覽](conceptual-overview.md)
- [檔指南](guide-to-the-documentation.md)
- [什麼是 Windows Communication Foundation](whats-wcf.md)
- [WCF 功能詳細資料](feature-details/index.md)
- [基本程式設計週期](basic-programming-lifecycle.md)
- [建立用戶端](building-clients.md)
- [基本 WCF 程式設計](basic-wcf-programming.md)
- [如何：建立雙工合約](feature-details/how-to-create-a-duplex-contract.md)
- [How to：使用雙工合約存取服務](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [System.servicemodel 中繼資料公用程式工具 ( # A0) ](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：使用 Svcutil.exe 下載元資料檔案](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [如何：使用設定檔發行服務的中繼資料](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [使用系結來設定服務和用戶端](using-bindings-to-configure-services-and-clients.md)
- [開始使用範例](samples/getting-started-sample.md)
- [Windows Communication Foundation 範例](samples/index.md)
- [自我裝載](samples/self-host.md)
