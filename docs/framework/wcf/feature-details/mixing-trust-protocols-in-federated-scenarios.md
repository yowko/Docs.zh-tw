---
title: 在聯合案例中混合信任通信協定
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248171"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="054d3-102">在聯合案例中混合信任通信協定</span><span class="sxs-lookup"><span data-stu-id="054d3-102">Mixing Trust Protocols in Federated Scenarios</span></span>

<span data-ttu-id="054d3-103">有些情況下，聯合用戶端會與信任版本不相同的服務和安全性權杖服務 (STS) 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="054d3-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="054d3-104">WSDL 服務可包含 `RequestSecurityTokenTemplate` 判斷提示 (Assertion)，其中 WS-Trust 項目的版本與 STS 不同。</span><span class="sxs-lookup"><span data-stu-id="054d3-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="054d3-105">在這種情況下，Windows Communication Foundation (WCF) 用戶端會將從收到的 WS-Trust 元素轉換 `RequestSecurityTokenTemplate` 成符合 STS 信任版本。</span><span class="sxs-lookup"><span data-stu-id="054d3-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="054d3-106">WCF 只會處理標準系結的不相符信任版本。</span><span class="sxs-lookup"><span data-stu-id="054d3-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="054d3-107">WCF 可辨識的所有標準演算法參數都是標準系結的一部分。</span><span class="sxs-lookup"><span data-stu-id="054d3-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="054d3-108">本主題說明服務和 STS 之間有各種信任設定的 WCF 行為。</span><span class="sxs-lookup"><span data-stu-id="054d3-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="054d3-109">RP Feb 2005 和 STS Feb 2005</span><span class="sxs-lookup"><span data-stu-id="054d3-109">RP Feb 2005 and STS Feb 2005</span></span>  

 <span data-ttu-id="054d3-110">信賴憑證者 (Relying Party，RP) WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="054d3-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="054d3-111">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="054d3-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="054d3-112">WCF 無法區分用戶端與服務參數;它會新增所有參數，並將它們傳送至 `RequestSecurityTokenTemplate` (RST) 。</span><span class="sxs-lookup"><span data-stu-id="054d3-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="054d3-113">RP Trust 1.3 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="054d3-113">RP Trust 1.3 and STS Trust 1.3</span></span>  

 <span data-ttu-id="054d3-114">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段內包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="054d3-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="054d3-115">用戶端組態檔所包含的 `secondaryParameters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="054d3-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="054d3-116">`EncryptionAlgorithm`如果專案內有，WCF `CanonicalizationAlgorithm` `KeyWrapAlgorithm` 會從 RST 下的最上層元素移除、和專案 `SecondaryParameters` 。</span><span class="sxs-lookup"><span data-stu-id="054d3-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="054d3-117">WCF 會將 `SecondaryParameters` 元素附加至未修改的外寄 RST。</span><span class="sxs-lookup"><span data-stu-id="054d3-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="054d3-118">RP Trust Feb 2005 和 STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="054d3-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  

 <span data-ttu-id="054d3-119">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="054d3-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 <span data-ttu-id="054d3-120">用戶端組態檔包含參數清單。</span><span class="sxs-lookup"><span data-stu-id="054d3-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="054d3-121">從用戶端設定檔中，WCF 無法區分服務與用戶端參數。</span><span class="sxs-lookup"><span data-stu-id="054d3-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="054d3-122">因此，WCF 會將所有參數轉換為信任版本1.3 命名空間。</span><span class="sxs-lookup"><span data-stu-id="054d3-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="054d3-123">WCF 會處理 `KeyType` 、和元素，如下所示 `KeySize` `TokenType` ：</span><span class="sxs-lookup"><span data-stu-id="054d3-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
- <span data-ttu-id="054d3-124">下載 WSDL，建立繫結，然後指派 RP 參數中的 `KeyType`、`KeySize` 和 `TokenType`。</span><span class="sxs-lookup"><span data-stu-id="054d3-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="054d3-125">用戶端組態檔隨即產生。</span><span class="sxs-lookup"><span data-stu-id="054d3-125">The client configuration file is then generated.</span></span>  
  
- <span data-ttu-id="054d3-126">現在用戶端可以變更組態檔中的任何參數。</span><span class="sxs-lookup"><span data-stu-id="054d3-126">The client can now change any parameter in the configuration file.</span></span>  
  
- <span data-ttu-id="054d3-127">在執行時間期間，WCF 會將所有指定的參數複製到 `AdditionalTokenParameters` 用戶端設定檔的區段中，但和除外， `KeyType` `KeySize` `TokenType` 因為這些參數是在設定檔產生期間所考慮的。</span><span class="sxs-lookup"><span data-stu-id="054d3-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="054d3-128">RP Trust 1.3 和 STS Trust Feb 2005</span><span class="sxs-lookup"><span data-stu-id="054d3-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  

 <span data-ttu-id="054d3-129">RP WSDL 在其 `RequestSecurityTokenTemplate` 區段中包含了下列項目：</span><span class="sxs-lookup"><span data-stu-id="054d3-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 <span data-ttu-id="054d3-130">用戶端組態檔所包含的 `secondaryParamters` 項目，會包裝 RP 所指定的參數。</span><span class="sxs-lookup"><span data-stu-id="054d3-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="054d3-131">WCF 會將區段內指定的所有參數複製 `SecondaryParameters` 到最上層 RST 元素，但不會將它們轉換成 2005 WS-Trust 命名空間。</span><span class="sxs-lookup"><span data-stu-id="054d3-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
