---
title: "HOW TO：建立自訂安全性權杖提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], providing credentials
ms.assetid: db8cb478-aa43-478b-bf97-c6489ad7c7fd
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e776b04c626fac134e2fc9c1b9fd0ae63a50b5d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-security-token-provider"></a>HOW TO：建立自訂安全性權杖提供者
這個主題會說明如何以自訂安全性權杖提供者建立新的權杖型別，以及如何整合提供者和自訂安全性權杖管理員。  
  
> [!NOTE]
>  如果在 <xref:System.IdentityModel.Tokens> 命名空間中，所找到的系統提供之權杖不符合您的需求，請建立自訂權杖提供者。  
  
 安全性權杖提供者會根據用戶端或服務認證中的資訊，建立安全性權杖表示。 若要在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性中使用自訂安全性權杖提供者，您必須建立自訂認證和安全性權杖管理員實作。  
  
 如需自訂認證和安全性權杖管理員的詳細資訊，請參閱[逐步解說： 建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。  
  
 如需有關認證的詳細資訊，安全性權杖管理員、 提供者和驗證器類別，請參閱[安全性架構](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)。  
  
### <a name="to-create-a-custom-security-token-provider"></a>建立自訂安全性權杖提供者  
  
1.  定義衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別的新類別。  
  
2.  實作 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> 方法。 這個方法會負責建立和傳回安全性權杖的執行個體。 下列範例會建立名稱為 `MySecurityTokenProvider` 的類別，並覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> 方法以傳回 <xref:System.IdentityModel.Tokens.X509SecurityToken> 類別的執行個體。 類別建構函式需要 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 類別的執行個體。  
  
     [!code-csharp[c_CustomTokenProvider#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#1)]
     [!code-vb[c_CustomTokenProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#1)]  
  
### <a name="to-integrate-a-custom-security-token-provider-with-a-custom-security-token-manager"></a>整合自訂安全性權杖提供者和自訂安全性權杖管理員  
  
1.  定義衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別的新類別。 (以下範例衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別，而這個類別則衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別)。  
  
2.  如果尚未覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 方法，請覆寫之。  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 方法會負責傳回 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別的執行個體，而這個執行個體適用於 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 安全性架構所傳遞至方法的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 參數。 使用適當的安全性權杖參數呼叫方法時，請修改方法以傳回自訂安全性權杖提供者實作 (在之前的程序中建立此實作)。 如需安全性權杖管理員的詳細資訊，請參閱[逐步解說： 建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。  
  
3.  將自訂邏輯新增至方法，讓方法可以根據 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 參數傳回自訂安全性權杖提供者。 下列範例會在符合權杖需求時，傳回自訂安全性權杖提供者。 這些需求包括 X.509 安全性權杖和訊息方向 (當權杖用於訊息輸出時)。 在其他情況下，程式碼會呼叫基底類別，以針對其他安全性權杖需求維護系統提供的行為。  
  
 [!code-csharp[c_CustomTokenProvider#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#2)]
 [!code-vb[c_CustomTokenProvider#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#2)]  
  
## <a name="example"></a>範例  
 下列範例會顯示完整 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 實作以及相對應的 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 實作。  
  
 [!code-csharp[c_CustomTokenProvider#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenprovider/cs/source.cs#0)]
 [!code-vb[c_CustomTokenProvider#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenprovider/vb/source.vb#0)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.IdentityModel.Selectors.SecurityTokenProvider>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.X509SecurityToken>  
 [逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [如何：建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [安全性架構](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
