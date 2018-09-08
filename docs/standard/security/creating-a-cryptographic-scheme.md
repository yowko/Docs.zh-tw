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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197889"
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="a44d8-102">建立密碼編譯配置</span><span class="sxs-lookup"><span data-stu-id="a44d8-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="a44d8-103">.NET Framework 的密碼編譯元件可以結合以建立不同的配置，來加密和解密資料。</span><span class="sxs-lookup"><span data-stu-id="a44d8-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="a44d8-104">加密和解密資料的簡單密碼編譯配置可能會指定下列步驟：</span><span class="sxs-lookup"><span data-stu-id="a44d8-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="a44d8-105">每一方產生一個公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a44d8-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="a44d8-106">各方交換他們的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="a44d8-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="a44d8-107">比方說，每一方產生 TripleDES 加密的祕密金鑰，並對方的公開金鑰加密新建立的金鑰。</span><span class="sxs-lookup"><span data-stu-id="a44d8-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="a44d8-108">每一方傳送資料至對方，並依特定順序合併對方的秘密金鑰與自己的秘密金鑰，建立新的秘密金鑰。</span><span class="sxs-lookup"><span data-stu-id="a44d8-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="a44d8-109">接著各方使用對稱加密開始交談。</span><span class="sxs-lookup"><span data-stu-id="a44d8-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="a44d8-110">建立密碼編譯配置不是簡單的工作。</span><span class="sxs-lookup"><span data-stu-id="a44d8-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="a44d8-111">如需有關使用密碼編譯的詳細資訊，請參閱 Platform SDK 文件中的密碼編譯 > 主題 http://msdn.microsoft.com/library。</span><span class="sxs-lookup"><span data-stu-id="a44d8-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44d8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a44d8-112">See also</span></span>

- [<span data-ttu-id="a44d8-113">The signature is valid</span><span class="sxs-lookup"><span data-stu-id="a44d8-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
