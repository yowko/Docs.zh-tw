---
title: 作法：建立自訂宣告
description: 瞭解如何在 WCF 中建立自訂宣告。 WCF 支援各種內建宣告，有些應用程式可能需要自訂宣告。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: ea3bc7384ca10538ca5ab1d3bb05da6a2757fb67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256010"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="ec7c8-104">作法：建立自訂宣告</span><span class="sxs-lookup"><span data-stu-id="ec7c8-104">How to: Create a Custom Claim</span></span>

<span data-ttu-id="ec7c8-105">Windows Communication Foundation (WCF) 中的身分識別模型基礎結構會提供一組內建的宣告類型和許可權，其中包含協助程式函式，可用來建立 <xref:System.IdentityModel.Claims.Claim> 具有這些類型和許可權的實例。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="ec7c8-106">這些內建宣告是設計用來建立 WCF 支援的用戶端認證類型中所找到的資訊模型。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="ec7c8-107">在許多情況下，內建宣告就已足夠；不過有些應用程式可能需要自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="ec7c8-108">宣告中包含了宣告類型、宣告適用的資源，以及擁有該資源所需的權限。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="ec7c8-109">這個主題會描述如何建立自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="ec7c8-110">依據基本資料型別建立自訂宣告</span><span class="sxs-lookup"><span data-stu-id="ec7c8-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="ec7c8-111">將宣告類型、資源值和權限傳遞至 <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> 建構函式，即可建立自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="ec7c8-112">決定用於宣告類型的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="ec7c8-113">宣告類型為唯一的字串識別碼。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="ec7c8-114">自訂宣告設計者的責任在於確保用於宣告類型的字串識別碼為獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="ec7c8-115">如需 WCF 所定義之宣告類型的清單，請參閱 <xref:System.IdentityModel.Claims.ClaimTypes> 類別。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="ec7c8-116">選擇基本資料型別和資源的值。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="ec7c8-117">資源就是物件。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-117">A resource is an object.</span></span> <span data-ttu-id="ec7c8-118">資源的 CLR 類型可以為基本，例如 <xref:System.String> 或 <xref:System.Int32>，或任何可序列化的類型。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="ec7c8-119">資源的 CLR 型別必須是可序列化的，因為宣告是在 WCF 的不同點進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="ec7c8-120">基本類型為可序列化。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="ec7c8-121">選擇由 WCF 定義的許可權，或自訂許可權的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="ec7c8-122">權限為唯一字串識別碼。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-122">A right is a unique string identifier.</span></span> <span data-ttu-id="ec7c8-123">由 WCF 定義的許可權定義于 <xref:System.IdentityModel.Claims.Rights> 類別中。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="ec7c8-124">自訂宣告設計者的責任在於確保用於權限的字串識別碼為獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="ec7c8-125">下列程式碼範例會使用 `http://example.org/claims/simplecustomclaim` 宣告類型，對名稱為 `Driver's License` 的資源建立自訂宣告，也會使用 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 權限建立自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="ec7c8-126">依據非基本資料型別建立自訂宣告</span><span class="sxs-lookup"><span data-stu-id="ec7c8-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="ec7c8-127">將宣告類型、資源值和權限傳遞至 <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> 建構函式，即可建立自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="ec7c8-128">決定用於宣告類型的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="ec7c8-129">宣告類型為唯一的字串識別碼。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="ec7c8-130">自訂宣告設計者的責任在於確保用於宣告類型的字串識別碼為獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="ec7c8-131">如需 WCF 所定義之宣告類型的清單，請參閱 <xref:System.IdentityModel.Claims.ClaimTypes> 類別。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="ec7c8-132">選擇或定義資源的可序列化非基本類型。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="ec7c8-133">資源就是物件。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-133">A resource is an object.</span></span> <span data-ttu-id="ec7c8-134">資源的 CLR 型別必須是可序列化的，因為宣告是在 WCF 的不同點進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="ec7c8-135">基本類型已為可序列化。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="ec7c8-136">定義新類型時，請將 <xref:System.Runtime.Serialization.DataContractAttribute> 套用至類別。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="ec7c8-137">也將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至需要序列化以做為宣告一部分之新類型的所有成員。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="ec7c8-138">下列程式碼範例會定義名稱為 `MyResourceType` 的自訂資源類型。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="ec7c8-139">選擇由 WCF 定義的許可權，或自訂許可權的唯一值。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="ec7c8-140">權限為唯一字串識別碼。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-140">A right is a unique string identifier.</span></span> <span data-ttu-id="ec7c8-141">由 WCF 定義的許可權定義于 <xref:System.IdentityModel.Claims.Rights> 類別中。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="ec7c8-142">自訂宣告設計者的責任在於確保用於權限的字串識別碼為獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="ec7c8-143">下列程式碼範例會使用 `http://example.org/claims/complexcustomclaim` 的宣告類型、`MyResourceType` 的自訂資源類型和 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 權限，建立自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="ec7c8-144">範例</span><span class="sxs-lookup"><span data-stu-id="ec7c8-144">Example</span></span>  

 <span data-ttu-id="ec7c8-145">下列程式碼範例會示範如何使用基本資源類型和非基本資源類型建立自訂宣告。</span><span class="sxs-lookup"><span data-stu-id="ec7c8-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="ec7c8-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec7c8-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="ec7c8-147">使用身分識別模型來管理宣告與授權</span><span class="sxs-lookup"><span data-stu-id="ec7c8-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
