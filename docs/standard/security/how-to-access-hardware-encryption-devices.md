---
title: HOW TO：存取硬體加密裝置
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33af618ac3971df76683fd64346e1aa1e5977177
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773411"
---
# <a name="how-to-access-hardware-encryption-devices"></a>HOW TO：存取硬體加密裝置
您可以使用 <xref:System.Security.Cryptography.CspParameters> 類別來存取硬體加密裝置。 例如，您可以使用這個類別來整合應用程式與智慧卡、硬體亂數產生器或特定密碼編譯演算法的硬體實作。  
  
 <xref:System.Security.Cryptography.CspParameters> 類別會建立存取正確安裝之硬體加密裝置的密碼編譯服務提供者 (CSP)。  您可以檢查下列登錄機碼使用登錄編輯程式 (Regedit.exe)，以驗證 CSP 的可用性：HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>使用金鑰卡簽署資料  
  
1. 建立 <xref:System.Security.Cryptography.CspParameters> 類別的新執行個體，並將整數提供者類型和提供者名稱傳遞給建構函式。  
  
2. 將適當的旗標傳遞給新建立之 <xref:System.Security.Cryptography.CspParameters> 物件的 <xref:System.Security.Cryptography.CspParameters.Flags%2A> 屬性。  例如，傳遞 <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> 旗標。  
  
3. 建立 <xref:System.Security.Cryptography.AsymmetricAlgorithm> 類別的新執行個體 (例如，<xref:System.Security.Cryptography.RSACryptoServiceProvider> 類別)，並傳遞 <xref:System.Security.Cryptography.CspParameters> 物件給建構函式。  
  
4. 使用其中一個 `Sign` 方法簽署資料，並使用其中一個 `Verify` 方法驗證資料。  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>使用硬體亂數產生器產生亂數  
  
1. 建立 <xref:System.Security.Cryptography.CspParameters> 類別的新執行個體，並將整數提供者類型和提供者名稱傳遞給建構函式。  
  
2. 建立 <xref:System.Security.Cryptography.RNGCryptoServiceProvider> 的新執行個體，並傳遞 <xref:System.Security.Cryptography.CspParameters> 物件給建構函式。  
  
3. 使用 <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> 或 <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> 方法建立亂數。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用智慧卡簽署資料。  程式碼範例會建立公開智慧卡的 <xref:System.Security.Cryptography.CspParameters> 物件，然後使用 CSP 初始化 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 物件。  程式碼範例接著會簽署並驗證某些資料。  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   包含 <xref:System> 和 <xref:System.Security.Cryptography> 命名空間。  
  
-   您的電腦上必須安裝智慧卡讀卡機和驅動程式。  
  
-   您必須使用讀卡機的特定資訊初始化 <xref:System.Security.Cryptography.CspParameters> 物件。  如需詳細資訊，請參閱讀卡機的文件。
