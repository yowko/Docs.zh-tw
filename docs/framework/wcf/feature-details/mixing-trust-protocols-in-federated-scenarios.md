---
title: 在聯合案例中混合信任通信協定
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494454"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="6bba2-102">在聯合案例中混合信任通信協定</span><span class="sxs-lookup"><span data-stu-id="6bba2-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="6bba2-103">有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="6bba2-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="6bba2-104">WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。</span><span class="sxs-lookup"><span data-stu-id="6bba2-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="6bba2-105">在這種情況下，Windows Communication Foundation (WCF) 用戶端會將從收到的 Ws-trust 元素轉換`RequestSecurityTokenTemplate`以符合 STS 信任版本。</span><span class="sxs-lookup"><span data-stu-id="6bba2-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="6bba2-106">WCF 會處理只能在標準繫結時不相符的信任版本。</span><span class="sxs-lookup"><span data-stu-id="6bba2-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="6bba2-107">WCF 所辨識的所有標準演算法參數是在標準繫結的一部分。</span><span class="sxs-lookup"><span data-stu-id="6bba2-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="6bba2-108">本主題描述與各種服務和 STS 之間的信任設定 WCF 行為。</span><span class="sxs-lookup"><span data-stu-id="6bba2-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="6bba2-109">RP Feb 2005 和 STS Feb 2005</span><span class="sxs-lookup"><span data-stu-id="6bba2-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="6bba2-110">信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="6bba2-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="6bba2-111">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="6bba2-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="6bba2-112">WCF 無法分辨用戶端和服務參數。它將所有的參數新增，並將它們傳送`RequestSecurityTokenTemplate`(RST)。</span><span class="sxs-lookup"><span data-stu-id="6bba2-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="6bba2-113">RP Trust 1.3 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="6bba2-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="6bba2-114">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段內包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="6bba2-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="6bba2-115">用戶端組態檔所包含的 `secondaryParameters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="6bba2-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="6bba2-116">WCF 會移除`EncryptionAlgorithm`，`CanonicalizationAlgorithm`和`KeyWrapAlgorithm`項目最上層的項目，如果是存在於在 RST 下從`SecondaryParameters`項目。</span><span class="sxs-lookup"><span data-stu-id="6bba2-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="6bba2-117">WCF 附加`SecondaryParameters`傳出的 RST 項目。</span><span class="sxs-lookup"><span data-stu-id="6bba2-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="6bba2-118">RP Trust Feb 2005 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="6bba2-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="6bba2-119">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="6bba2-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="6bba2-120">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="6bba2-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="6bba2-121">從用戶端組態檔中，WCF 無法分辨服務和用戶端的參數。</span><span class="sxs-lookup"><span data-stu-id="6bba2-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="6bba2-122">因此 WCF 會將所有參數都轉換成信任 1.3 版命名空間。</span><span class="sxs-lookup"><span data-stu-id="6bba2-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="6bba2-123">WCF 的控制代碼`KeyType`， `KeySize`，和`TokenType`項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="6bba2-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="6bba2-124">下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。</span><span class="sxs-lookup"><span data-stu-id="6bba2-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="6bba2-125">用戶端組態檔隨即產生。</span><span class="sxs-lookup"><span data-stu-id="6bba2-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="6bba2-126">現在用戶端可以變更組態檔中的任何參數。</span><span class="sxs-lookup"><span data-stu-id="6bba2-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="6bba2-127">在執行階段，WCF 會複製到指定的所有參數`AdditionalTokenParameters`除了用戶端組態檔區段`KeyType`，`KeySize`和`TokenType`，因為這些參數都計算在內的組態檔期間層代。</span><span class="sxs-lookup"><span data-stu-id="6bba2-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="6bba2-128">RP Trust 1.3 和 STS Trust Feb 2005</span><span class="sxs-lookup"><span data-stu-id="6bba2-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="6bba2-129">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="6bba2-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="6bba2-130">用戶端組態檔所包含的 `secondaryParamters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="6bba2-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="6bba2-131">WCF 複製內指定的所有參數`SecondaryParameters`區段的最上層 RST 項目，但不會將它們轉換成 2005 Ws-trust 命名空間。</span><span class="sxs-lookup"><span data-stu-id="6bba2-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
