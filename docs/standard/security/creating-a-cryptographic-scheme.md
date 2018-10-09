---
title: 建立密碼編譯配置
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51d07fadcf359c2b44f22ca9868d0f12e24b80c5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873111"
---
# <a name="creating-a-cryptographic-scheme"></a>建立密碼編譯配置
.NET Framework 的密碼編譯元件可以結合以建立不同的配置，來加密和解密資料。  
  
 加密和解密資料的簡單密碼編譯配置可能會指定下列步驟：  
  
1.  每一方產生一個公開/私密金鑰組。  
  
2.  各方交換他們的公開金鑰。  
  
3.  比方說，每一方產生 TripleDES 加密的祕密金鑰，並對方的公開金鑰加密新建立的金鑰。  
  
4.  每一方傳送資料至對方，並依特定順序合併對方的秘密金鑰與自己的秘密金鑰，建立新的秘密金鑰。  
  
5.  接著各方使用對稱加密開始交談。  
  
 建立密碼編譯配置不是簡單的工作。
  
## <a name="see-also"></a>另請參閱

- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
