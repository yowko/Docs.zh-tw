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
ms.openlocfilehash: 2db6d4229ac777801aff792c86fe0e5e9a1b4994
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964380"
---
# <a name="creating-a-cryptographic-scheme"></a>建立密碼編譯配置
.NET Framework 的密碼編譯元件可以結合以建立不同的配置，來加密和解密資料。  
  
 加密和解密資料的簡單密碼編譯配置可能會指定下列步驟：  
  
1.  每一方產生一個公開/私密金鑰組。  
  
2.  各方交換他們的公開金鑰。  
  
3.  比方說，每一方產生 TripleDES 加密的祕密金鑰，並對方的公開金鑰加密新建立的金鑰。  
  
4.  每一方傳送資料至對方，並依特定順序合併對方的秘密金鑰與自己的秘密金鑰，建立新的秘密金鑰。  
  
5.  接著各方使用對稱加密開始交談。  
  
 建立密碼編譯配置不是簡單的工作。 如需有關使用密碼編譯的詳細資訊，請參閱 Platform SDK 文件中的密碼編譯 > 主題 http://msdn.microsoft.com/library。  
  
## <a name="see-also"></a>另請參閱

- [The signature is valid](../../../docs/standard/security/cryptographic-services.md)
