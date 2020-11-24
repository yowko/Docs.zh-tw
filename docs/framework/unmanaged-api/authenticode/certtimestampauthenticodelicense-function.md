---
title: CertTimestampAuthenticodeLicense 函式
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
ms.openlocfilehash: fc1a99572406a38aee8133d6435134b78a134175
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674095"
---
# <a name="certtimestampauthenticodelicense-function"></a>CertTimestampAuthenticodeLicense 函式

為 Authenticode XrML 授權加上時間戳記。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>參數  

 `pSignedLicenseBlob`  
 [in] 要加上時間戳記的已簽署 Authenticode XrML 授權。 請參閱 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) 結構。  
  
 `pwszTimestampURI`  
 [in] 時間戳記伺服器的 URI。  
  
 `pTimestampSignatureBlob`  
 [out] CRYPT_DATA_BLOB (要接收 Base 64 編碼的時間戳記簽章) 的指標。 在 `pTimestampSignatureBlob` -> `pbData` 使用之後，呼叫者必須負責釋放 `HepFree()` 。 請參閱 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) 結構。  
  
## <a name="remarks"></a>備註  

 時間戳記簽章實際上是 PKCS #7 SignedData 訊息，其內容是來自授權簽章的 SignatureValue 二進位格式。 基本上是將此當作授權的副署。  
  
## <a name="return-value"></a>傳回值  

 如果函式成功，會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](index.md)
