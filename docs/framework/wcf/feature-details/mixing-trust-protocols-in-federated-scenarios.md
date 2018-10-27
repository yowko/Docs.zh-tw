---
title: 在聯合案例中混合信任通信協定
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: ce5c3a1875d84d98068dcc78d8346a88bc0b28f3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182902"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="cd7b8-102">在聯合案例中混合信任通信協定</span><span class="sxs-lookup"><span data-stu-id="cd7b8-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="cd7b8-103">有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="cd7b8-104">WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="cd7b8-105">在這種情況下，Windows Communication Foundation (WCF) 用戶端會將從收到的 Ws-trust 元素轉換`RequestSecurityTokenTemplate`成符合 STS 信任版本。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="cd7b8-106">WCF 會處理只能在標準繫結時不相符的信任版本。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="cd7b8-107">WCF 所辨識的所有標準演算法參數是標準繫結的一部分。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="cd7b8-108">本主題說明使用各種服務與 STS 之間的信任設定 WCF 行為。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="cd7b8-109">RP Feb 2005 和 STS Feb 2005</span><span class="sxs-lookup"><span data-stu-id="cd7b8-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="cd7b8-110">信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="cd7b8-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="cd7b8-111">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="cd7b8-112">WCF 無法分辨用戶端和服務的參數;它將所有參數，並將它們傳送`RequestSecurityTokenTemplate`(RST)。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="cd7b8-113">RP Trust 1.3 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="cd7b8-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="cd7b8-114">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段內包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="cd7b8-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="cd7b8-115">用戶端組態檔所包含的 `secondaryParameters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="cd7b8-116">WCF 會移除`EncryptionAlgorithm`，`CanonicalizationAlgorithm`並`KeyWrapAlgorithm`項目最上層的項目，如果這些是存在於在 RST 下從`SecondaryParameters`項目。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="cd7b8-117">WCF 會附加`SecondaryParameters`傳出的 RST 項目。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="cd7b8-118">RP Trust Feb 2005 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="cd7b8-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="cd7b8-119">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="cd7b8-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="cd7b8-120">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="cd7b8-121">從用戶端組態檔中，WCF 無法分辨服務和用戶端的參數而定。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="cd7b8-122">因此 WCF 會將所有參數都轉換成信任 1.3 版命名空間。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="cd7b8-123">WCF 的控制代碼`KeyType`， `KeySize`，和`TokenType`項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cd7b8-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="cd7b8-124">下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="cd7b8-125">用戶端組態檔隨即產生。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="cd7b8-126">現在用戶端可以變更組態檔中的任何參數。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="cd7b8-127">在執行階段，WCF 會複製到指定的所有參數`AdditionalTokenParameters`以外的用戶端組態檔區段`KeyType`，`KeySize`和`TokenType`，這些參數會包含在組態檔，因此層代。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="cd7b8-128">RP Trust 1.3 和 STS Trust Feb 2005</span><span class="sxs-lookup"><span data-stu-id="cd7b8-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="cd7b8-129">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="cd7b8-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="cd7b8-130">用戶端組態檔所包含的 `secondaryParamters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="cd7b8-131">WCF 會將內指定的所有參數都複製`SecondaryParameters`區段最上層 RST 項目，但不會將它們轉換成 2005 Ws-trust 命名空間。</span><span class="sxs-lookup"><span data-stu-id="cd7b8-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
