---
title: 進階強式命名
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cbda9c160b99bf5648c670a67d39b245f031645
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59319868"
---
# <a name="enhanced-strong-naming"></a>進階強式命名
強式名稱簽章是 .NET Framework 中的身分識別機制，用來識別組件。 它是公開金鑰數位簽章，通常用來驗證從建立者 (簽署者) 傳遞給收件者 (驗證者) 的資料完整性。 此簽章用來當作組件的唯一身分識別，並可確保對組件的參考不會模稜兩可。 組件在建置程序的一部分簽署，然後在載入時加以驗證。  
  
 強式名稱簽章可協助防止惡徒竄改組件，然後使用原始簽署者的金鑰重新簽署組件。 不過，強式名稱金鑰並不包含關於發行者的任何可靠資訊，也不包含憑證階層。 強式名稱簽章不保證簽署組件之人的可信度，或指出該人是否為金鑰的合法擁有者；它僅指出金鑰的擁有者簽署了該組件。 因此，我們不建議使用強式名稱簽章作為安全性驗證而來信任協力廠商程式碼。 Microsoft Authenticode 是驗證程式碼的建議方式。  
  
## <a name="limitations-of-conventional-strong-names"></a>傳統強式名稱的限制  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前的版本所使用的強式命名技術有下列缺點：  
  
-   金鑰經常受到攻擊，改善的技術和硬體能夠更輕鬆從公開金鑰推斷私密金鑰。 為了防範攻擊，必須使用較大的金鑰。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前的 .NET Framework 版本，可讓您以任何大小的金鑰 (預設大小為 1024 位元) 簽署，但使用新的金鑰簽署組件會中斷參考組件較舊身分識別的所有二進位檔。 因此，如果您想要維護相容性，很難升級簽署金鑰的大小。  
  
-   強式名稱簽署只支援 SHA-1 演算法。 最近已發現 SHA-1 不足以應付安全雜湊應用程式。 因此，必須使用更強的演算法 (SHA-256 或以上)。 很可能 SHA-1 會失去其與 FIPS 相容的地位，如此對於選擇只使用與 FIPS 相容的軟體和演算法的人會造成問題。  
  
## <a name="advantages-of-enhanced-strong-names"></a>增強強式名稱的優點  
 增強強式名稱的主要優點是與預先存在的強式名稱相容，以及能夠宣告一個身分識別相當於另一個身分識別：  
  
-   有預先存在的已簽署組件的開發人員，可以將他們的身分識別移轉至 SHA-2 演算法，同時維持與參考舊身分識別的組件相容性。  
  
-   建立新組件而且不在意預先存在的強式名稱簽章的開發人員，可以使用更安全的 SHA-2 演算法，並如往常般簽署組件。  
  
## <a name="using-enhanced-strong-names"></a>使用進階強式名稱  
 強式名稱金鑰包含簽章金鑰和身分識別金鑰。 組件以簽章金鑰簽署，而以身分識別金鑰識別。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前，這兩個金鑰完全相同。 從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，身分識別金鑰保留與較早 .NET Framework 版本中的相同，但簽章金鑰已經使用更強的雜湊演算法增強。 此外，簽章金鑰以身分識別金鑰簽署，以便建立副署。  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性讓組件中繼資料能使用預先存在的公開金鑰處理組件身分識別，如此能讓舊組件參考繼續運作。  <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性使用副署來確保新簽章金鑰的擁有者也是舊身分識別金鑰的擁有者。  
  
### <a name="signing-with-sha-2-without-key-migration"></a>使用 SHA-2 簽署，而不需要金鑰移轉  
 從命令提示字元視窗中執行下列命令簽署組件，而不移轉強式名稱簽章：  
  
1. (如有必要) 產生新的身分識別金鑰。  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2. 取得身分識別公開金鑰，並指定使用此金鑰簽署時，應該使用 SHA-2 演算法。  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. 使用身分識別公用金鑰檔案延遲簽署組件。  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. 使用完整身分識別金鑰組重新簽署組件。  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>使用 SHA-2 簽署，並且進行金鑰移轉  
 從命令提示字元視窗中執行下列命令，使用移轉的強式名稱簽章來簽署組件。  
  
1. (如有必要) 產生身分識別與簽章金鑰組。  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. 取得簽章公開金鑰，並指定使用此金鑰簽署時，應該使用 SHA-2 演算法。  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. 取得身分識別公開金鑰，它決定產生副署的雜湊演算法。  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. 產生 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性的參數，然後將屬性附加至組件。  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    這會產生類似下列內容的輸出。

    ```
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    此輸出即會轉換成 AssemblySignatureKeyAttribute。

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. 使用身分識別公用金鑰延遲簽署組件。  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. 使用簽章金鑰組完整簽署組件。  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>另請參閱

- [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
