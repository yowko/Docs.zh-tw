---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c63e1b3de464b306f46e2f0935b1208d7262925a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274188"
---
# <a name="clientcredentials"></a><span data-ttu-id="a2f7f-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a2f7f-102">ClientCredentials</span></span>

<span data-ttu-id="a2f7f-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="a2f7f-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f7f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a2f7f-104">Syntax</span></span>  
  
```csharp
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a2f7f-105">方法</span><span class="sxs-lookup"><span data-stu-id="a2f7f-105">Methods</span></span>  

 <span data-ttu-id="a2f7f-106">ClientCredentials 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a2f7f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a2f7f-107">Properties</span></span>  

 <span data-ttu-id="a2f7f-108">ClientCredentials 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a2f7f-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="a2f7f-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="a2f7f-109">ClientCertificate</span></span>  

 <span data-ttu-id="a2f7f-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-110">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-112">用戶端用來向服務驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="a2f7f-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="a2f7f-113">HttpDigest</span></span>  

 <span data-ttu-id="a2f7f-114">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-114">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-116">目前的 Http 摘要式認證。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="a2f7f-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="a2f7f-117">IssuedToken</span></span>  

 <span data-ttu-id="a2f7f-118">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-118">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-120">用來聯繫本機安全性權杖服務的端點位址與繫結。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="a2f7f-121">對等</span><span class="sxs-lookup"><span data-stu-id="a2f7f-121">Peer</span></span>  

 <span data-ttu-id="a2f7f-122">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-122">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-124">對等節點用來向 mesh 中的其他節點驗證自己時使用的認證。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="a2f7f-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="a2f7f-125">ServiceCertificate</span></span>  

 <span data-ttu-id="a2f7f-126">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-126">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-128">服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="a2f7f-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="a2f7f-129">SupportInteractive</span></span>  

 <span data-ttu-id="a2f7f-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="a2f7f-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="a2f7f-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-132">指定認證是否支援互動式交涉的布林值。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="a2f7f-133">UserName</span><span class="sxs-lookup"><span data-stu-id="a2f7f-133">UserName</span></span>  

 <span data-ttu-id="a2f7f-134">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-134">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-136">用戶端用來向服務驗證自身的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="a2f7f-137">Windows</span><span class="sxs-lookup"><span data-stu-id="a2f7f-137">Windows</span></span>  

 <span data-ttu-id="a2f7f-138">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="a2f7f-138">Data type: string</span></span>  
  
 <span data-ttu-id="a2f7f-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a2f7f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a2f7f-140">用戶端用來向服務驗證自身的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f7f-141">規格需求</span><span class="sxs-lookup"><span data-stu-id="a2f7f-141">Requirements</span></span>  
  
|<span data-ttu-id="a2f7f-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a2f7f-142">MOF</span></span>|<span data-ttu-id="a2f7f-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a2f7f-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a2f7f-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="a2f7f-144">Namespace</span></span>|<span data-ttu-id="a2f7f-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a2f7f-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2f7f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2f7f-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
