---
title: 教程：開始使用 Windows 通信基礎應用程式
description: 這些教程提供了創建 WCF 應用程式的介紹。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: df73f953372202796cebce9d3e3f28bd617c67ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184115"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>教程：開始使用 Windows 通信基礎應用程式
以下一系列教程將向您介紹 Windows 通信基礎 （WCF） 程式設計體驗。 按順序完成這些教程將為您提供對創建 WCF 應用程式所需的步驟的介紹性理解。 完成後，您將有一個正在運行的 WCF 服務和一個 WCF 用戶端調用該服務。

本教程假定您正在使用 Visual Studio 作為開發環境。 如果您正在使用其他開發環境，請忽略特定于 Visual Studio 的說明。

有關可以下載和運行的示例 WCF 應用程式，請參閱[Windows 通信基礎示例](samples/index.md)。 有關示例的介紹，請參閱[入門示例](samples/getting-started-sample.md)。

有關創建服務和用戶端的深入資訊，請參閱[基本 WCF 程式設計](basic-wcf-programming.md)。

## <a name="wcf-tutorials"></a>WCF 教程

前三個教程介紹如何定義 WCF 服務協定、如何實現它以及如何託管它。 您創建的服務在主控台應用程式中自託管。 您還可以在 Microsoft 互聯網資訊服務 （IIS） 下託管服務。 有關詳細資訊，請參閱[如何：在 IIS 中託管 WCF 服務](feature-details/how-to-host-a-wcf-service-in-iis.md)。 儘管在本教程中使用代碼佈建服務，但您也可以[在設定檔中佈建服務](configuring-services-using-configuration-files.md)。

- [教程：定義服務協定](how-to-define-a-wcf-service-contract.md)

    使用使用者定義的介面創建 WCF 協定。 此協定定義服務公開的功能。

- [教程：實現服務合同](how-to-implement-a-wcf-contract.md)

    定義協定後，必須使用服務類實現它。

- [教程：託管並運行基本服務](how-to-host-and-run-a-basic-wcf-service.md)

    佈建服務的終結點，並在主控台應用程式中託管服務。 要使服務處於活動狀態，必須配置該服務並在運行時環境中託管它。 此運行時環境創建服務並控制其上下文和存留期。

接下來的兩個教程介紹如何創建、配置和使用用戶端應用程式來調用服務公開的操作。 服務會發行定義用戶端應用程式與服務進行通訊所需之資訊的中繼資料。 Visual Studio 自動訪問此中繼資料的過程，並用它來構造服務的用戶端應用程式。 如果您決定不使用 Visual Studio，則可以使用[服務模型中繼資料實用程式工具 （*Svcutil.exe*）。](servicemodel-metadata-utility-tool-svcutil-exe.md)

- [教程：創建用戶端](how-to-create-a-wcf-client.md)

    檢索中繼資料以從 WCF 服務創建 WCF 用戶端代理。 通過使用 Visual Studio 添加服務引用來檢索中繼資料，或者可以使用服務模型中繼資料實用程式工具。 指定用戶端用於訪問服務的終結點。

- [教程：使用用戶端](how-to-use-a-wcf-client.md)

    使用 WCF 用戶端代理調用服務操作。

## <a name="reference"></a>參考

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>另請參閱

- [概念概觀](conceptual-overview.md)
- [文檔指南](guide-to-the-documentation.md)
- [什麼是 Windows 通信基礎](whats-wcf.md)
- [WCF 功能詳細資訊](feature-details/index.md)
- [基本程式設計生命週期](basic-programming-lifecycle.md)
- [構建用戶端](building-clients.md)
- [基本 WCF 程式設計](basic-wcf-programming.md)
- [如何：創建雙工協定](feature-details/how-to-create-a-duplex-contract.md)
- [如何：使用雙工協定訪問服務](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [服務模型中繼資料實用程式工具 （Svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：使用 Svcutil.exe 下載中繼資料文檔](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [如何：使用設定檔發佈服務的中繼資料](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [使用綁定佈建服務和用戶端](using-bindings-to-configure-services-and-clients.md)
- [入門示例](samples/getting-started-sample.md)
- [Windows 通信基礎示例](samples/index.md)
- [自我裝載](samples/self-host.md)
