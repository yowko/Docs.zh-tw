---
title: 整合 COM 應用程式概觀
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 99e3c2f4445673f3b74048a2b466203af7bc2795
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045887"
---
# <a name="integrating-with-com-applications-overview"></a>整合 COM 應用程式概觀

Windows Communication Foundation (WCF) 提供 managed 程式碼開發人員豐富的環境, 讓您建立連線的應用程式。 不過, 如果您有大量的非受控 COM 程式碼投資, 而且不想要遷移, 您仍然可以使用 WCF 服務標記, 將 WCF Web 服務直接整合到現有的程式碼中。 服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。

> [!NOTE]
> 服務名字標記會使用 WCF 通道來進行所有通訊。 該通道的安全性和識別機制不同於標準 COM 和 DCOM Proxy 所使用的機制。 此外, 因為服務名字標記會使用 WCF 通道, 所以所有呼叫的預設超時時間為一分鐘。

服務標記會與`GetObject`函式搭配使用, 以針對呼叫 WCF Web 服務的強型別 COM 特定方法提供非受控開發人員。 這需要 WCF Web 服務合約的本機 COM 可見定義, 以及要使用的系結。 就像其他 WCF 用戶端一樣, 服務名字標記必須為服務建立具類型的通道, 雖然此通道結構會在第一次方法呼叫時, 以透明方式對 COM 程式設計人員進行。

與其他 WCF 用戶端共通的是, 使用名字標記時, 應用程式會指定要與服務通訊的位址、系結和合約。 可以使用下列其中一種方法指定合約：

- 型別合約：合約會在用戶端電腦上註冊為 COM 可見型別。

- WSDL 合約：合約會以 WSDL 文件的形式提供。

- MEX 合約：合約會在執行階段從中繼資料交換 (MEX) 端點擷取。

## <a name="parameters-supported-by-the-service-moniker"></a>服務 Moniker 支援的參數

下表顯示服務 Moniker 所支援的參數。

|參數|描述|
|---------------|-----------------|
|`address`|服務的 URL 位置。|
|`binding`|應用程式組態中的繫結區段名稱。|
|`bindingConfiguration`|具名繫結區段中的具名繫結執行個體。|
|`contract`|介面識別項 (IID)，表示服務合約或合約名稱 (來自 MEX)。|
|`wsdl`|WSDL 文件，提供其他形式的合約定義。|
|`spnIdentity`|伺服器主要名稱 (SPN) 身分識別，用於與服務進行通訊。|
|`upnIdentity`|使用者主要名稱 (UPN) 身分識別，用於與服務進行通訊。|
|`dnsIdentity`|DNS 身分識別，用於與服務進行通訊。|
|`mexAddress`|服務中繼資料交換 (MEX) 端點的 URL 位置。|
|`mexBinding`|要連接 MEX 端點之應用程式組態中的繫結區段名稱。|
|`mexBindingConfiguration`|要連接 MEX 端點之具名繫結區段中的具名繫結執行個體。|
|`bindingNamespace`|在擷取的 MEX 中，繫結區段名稱的命名空間。|
|`contractNamespace`|在擷取的 MEX 中，合約的命名空間。|
|`mexSpnIdentity`|伺服器主要名稱 (SPN) 身分識別，用於與 MEX 端點進行通訊。|
|`mexUpnIdentity`|使用者主要名稱 (UPN) 身分識別，用於與 MEX 端點進行通訊。|
|`mexDnsIdentity`|DNS 身分識別，用於與 MEX 端點進行通訊。|
|`serializer`|指定要使用 "xml" 或 "datacontract" 序列化程式。|

> [!NOTE]
> 即使與完全以 COM 為基礎的用戶端搭配使用, 服務的名字標記還是必須在用戶端電腦上安裝 WCF 和支援的 .NET Framework 2.0。 此外，使用服務 Moniker 的用戶端應用程式也一定要載入適當版本的 .NET Framework 執行階段。 在 Office 應用程式中使用 Moniker 時，可能需要有組態檔來確認是否載入了正確的 Framework 版本。 例如，在 Excel 中應將下列文字放入與 Excel.exe 檔案位在相同的目錄下，而且名為 Excel.exe.config 的檔案中：
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a>另請參閱

- [如何：註冊並設定服務標記](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
