---
title: "在聯合案例中混合信任通信協定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="f1500-102">在聯合案例中混合信任通信協定</span><span class="sxs-lookup"><span data-stu-id="f1500-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="f1500-103">有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="f1500-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="f1500-104">WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。</span><span class="sxs-lookup"><span data-stu-id="f1500-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="f1500-105">在這個情況下，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端會將從 `RequestSecurityTokenTemplate` 收到的 WS-Trust 元素轉換成符合 STS 信任版本。</span><span class="sxs-lookup"><span data-stu-id="f1500-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f1500-106"> 只會處理標準繫結的不相符信任版本。</span><span class="sxs-lookup"><span data-stu-id="f1500-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="f1500-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以識別的所有標準演算法參數都包含在標準繫結中。</span><span class="sxs-lookup"><span data-stu-id="f1500-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="f1500-108">本主題將透過該服務和 STS 之間的各種信任設定來說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的行為。</span><span class="sxs-lookup"><span data-stu-id="f1500-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="f1500-109">RP Feb 2005 和 STS Feb 2005</span><span class="sxs-lookup"><span data-stu-id="f1500-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="f1500-110">信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="f1500-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="f1500-111">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="f1500-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f1500-112"> 無法分辨用戶端和服務的參數，因此它會加入所有參數，並以 `RequestSecurityTokenTemplate` (RST) 傳送這些參數。</span><span class="sxs-lookup"><span data-stu-id="f1500-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="f1500-113">RP Trust 1.3 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="f1500-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="f1500-114">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段內包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="f1500-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="f1500-115">用戶端組態檔所包含的 `secondaryParameters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="f1500-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="f1500-116">如果 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元素中有 `EncryptionAlgorithm`、`CanonicalizationAlgorithm` 和 `KeyWrapAlgorithm` 元素，則 `SecondaryParameters` 會在 RST 下從最上層元素移除這些元素。</span><span class="sxs-lookup"><span data-stu-id="f1500-116">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f1500-117"> 會將 `SecondaryParameters` 元素原封不動地附加至傳出的 RST。</span><span class="sxs-lookup"><span data-stu-id="f1500-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="f1500-118">RP Trust Feb 2005 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="f1500-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="f1500-119">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="f1500-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="f1500-120">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="f1500-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="f1500-121">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 無法從用戶端組態檔分辨服務和用戶端的參數。</span><span class="sxs-lookup"><span data-stu-id="f1500-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="f1500-122">因此 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將所有參數轉換成 Trust 1.3 版命名空間 (Namespace)。</span><span class="sxs-lookup"><span data-stu-id="f1500-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f1500-123"> 會處理 `KeyType`、`KeySize` 和 `TokenType` 項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f1500-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="f1500-124">下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。</span><span class="sxs-lookup"><span data-stu-id="f1500-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="f1500-125">用戶端組態檔隨即產生。</span><span class="sxs-lookup"><span data-stu-id="f1500-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="f1500-126">現在用戶端可以變更組態檔中的任何參數。</span><span class="sxs-lookup"><span data-stu-id="f1500-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="f1500-127">在執行階段期間，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會將指定的所有參數複製到用戶端組態檔的 `AdditionalTokenParameters` 區段，但不包括 `KeyType`、`KeySize` 和 `TokenType`，因為這些參數已經在產生組態檔期間執行過任務。</span><span class="sxs-lookup"><span data-stu-id="f1500-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="f1500-128">RP Trust 1.3 和 STS Trust Feb 2005</span><span class="sxs-lookup"><span data-stu-id="f1500-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="f1500-129">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="f1500-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="f1500-130">用戶端組態檔所包含的 `secondaryParamters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="f1500-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f1500-131"> 會將指定於 `SecondaryParameters` 區段內的所有參數複製到最上層 RST 項目，但是不會將這些參數轉換成 2005 WS-Trust 命名空間。</span><span class="sxs-lookup"><span data-stu-id="f1500-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
