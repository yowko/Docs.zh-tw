---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963967"
---
# <a name="clientcredentials"></a>ClientCredentials
ClientCredentials  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="methods"></a>方法  
 ClientCredentials 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 ClientCredentials 類別具有下列屬性：  
  
### <a name="clientcertificate"></a>ClientCertificate  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端用來向服務驗證的 X.509 憑證。  
  
### <a name="httpdigest"></a>HttpDigest  
 資料型別：字串  
  
 存取類型：唯讀  
  
 目前的 Http 摘要式認證。  
  
### <a name="issuedtoken"></a>IssuedToken  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用來聯繫本機安全性權杖服務的端點位址與繫結。  
  
### <a name="peer"></a>對等  
 資料型別：字串  
  
 存取類型：唯讀  
  
 對等節點用來向 mesh 中的其他節點驗證自己時使用的認證。  
  
### <a name="servicecertificate"></a>ServiceCertificate  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務的 X.509 憑證。  
  
### <a name="supportinteractive"></a>SupportInteractive  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定認證是否支援互動式交涉的布林值。  
  
### <a name="username"></a>使用者名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端用來向服務驗證自身的使用者名稱和密碼。  
  
### <a name="windows"></a>Windows  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用戶端用來向服務驗證自身的 Windows 認證。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ClientCredentials>
