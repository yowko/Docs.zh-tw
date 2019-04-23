---
title: Sn.exe (強式名稱工具)
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a8c7ce090b286db9d86e0fc6c54ae33e7e2d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191883"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (強式名稱工具)
強式名稱工具 (Sn.exe) 可幫助您使用[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)簽署組件。 Sn.exe 提供了金鑰管理、簽章產生和簽章驗證的選項。  
  
> [!WARNING]
> 請勿依賴強式名稱提供安全性。 強式名稱僅提供唯一識別。

 如需強式命名和強式名稱組件的詳細資訊，請參閱[強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)和[如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。  
  
 強式名稱工具會隨 Visual Studio 自動安裝。 若要啟動這項工具，請使用開發人員命令提示字元 (或 Windows 7 中的 Visual Studio 命令提示字元)。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  

> [!NOTE]
>  在 64 位元電腦上，請使用 Visual Studio 開發人員命令提示字元執行 Sn.exe 的 32 位元版本，且使用 Visual Studio x64 Win64 命令提示字元執行 64 位元版本。 
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>參數  
  
|選項|說明|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|產生 <xref:System.Reflection.AssemblySignatureKeyAttribute> 資料，將識別金鑰從檔案移轉到簽章金鑰。|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|產生 <xref:System.Reflection.AssemblySignatureKeyAttribute> 資料，將識別金鑰從金鑰容器移轉到簽章金鑰。|  
|**-c** [*csp*]|設定預設的密碼編譯服務提供者 (CSP) 用於強式名稱簽署。 此設定會套用到整部電腦。 如果您未指定 CSP 名稱，Sn.exe 會清除目前設定。|  
|**-d** *container*|從強式名稱 CSP 刪除指定的金鑰容器。|  
|**-D**  *assembly1 assembly2*|驗證兩個組件只有簽章不同。 通常在組件以不同的金鑰組重新簽署後，會使用這種方式進行檢查。|  
|**-e**  *assembly outfile*|從 *assembly* 擷取公開金鑰，然後將它存放到 *outfile* 中。|  
|**-h**|顯示工具的命令語法和選項。|  
|**-i** *infile container*|從指定的金鑰容器 *infile* 安裝金鑰組。 金鑰容器位於強式名稱 CSP 內。|  
|**-k** [*keysize*] *outfile*|產生指定大小的新 <xref:System.Security.Cryptography.RSACryptoServiceProvider> 金鑰，並將它寫入指定的檔案中。  公開和私密金鑰都會寫入檔案中。<br /><br /> 如果您未指定金鑰大小，在已安裝 Microsoft 增強型密碼編譯提供者的情況下，預設會產生 1,024 位元的金鑰，否則會產生 512 位元的金鑰。<br /><br /> 如果已安裝 Microsoft 增強型密碼編譯提供者，則 *keysize* 參數可支援的金鑰長度為從 384 位元至 16,384 位元，並以 8 位元為增量單位。  如果您安裝的是 Microsoft 基底密碼編譯提供者，則該參數可支援的金鑰長度是從 384 位元到 512 位元，並以 8 位元為增量單位。|  
|**-m** [**y** *&#124;* **n**]|指定金鑰容器是電腦專屬或使用者專屬。 如果您指定 *y*，表示金鑰容器為電腦專屬。 如果您指定 *n*，表示金鑰容器是使用者專屬。<br /><br /> 如果 y 和 n 都沒有指定，則此選項會顯示目前設定。|  
|**-o**  *infile* [*outfile*]|從 *infile* 擷取公開金鑰，然後存放到 .csv 檔案中。 公開金鑰的每一個位元組會以逗號分隔。 此格式對於將金鑰參考硬式編碼為原始程式碼中的初始化陣列而言很實用。 如果您未指定 *outfile*，此選項會將輸出放置到 [剪貼簿]。 **注意：** 此選項不會驗證輸入是否只是公開金鑰。 如果 `infile` 包含具有私密金鑰的金鑰組，則也會擷取該私密金鑰。|  
|**-p** *infile outfile* [*hashalg*]|選擇性地使用 *hashalg* 指定的 RSA 演算法從 *infile* 中的金鑰組擷取公開金鑰，並將它儲存在 *outfile* 中。 您可以使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 的 **/delaysign+** 和 **/keyfile** 選項，將這個公開金鑰用於延遲簽署組件。 延遲簽署組件時，在編譯時期只會設定公開金鑰，而檔案中會為簽章保留空間，以便稍後知道私密金鑰時再加入簽章。|  
|**-pc**  *container* *outfile* [*hashalg*]|從 *container* 中的金鑰組擷取公開金鑰，並且將它儲存在 *outfile* 中。 如果您使用 *hashalg* 選項，則會使用 RSA 演算法擷取公開金鑰。|  
|**-Pb** [**y** *&#124;* **n**]|指定是否強制執行強式名稱略過原則。 如果指定 *y*，則將完全信任組件載入至完全信任的 <xref:System.AppDomain> 時，就不會驗證其強式名稱。 如果指定 *n*，就會驗證強式名稱的正確性，但不是針對特定的強式名稱進行驗證。 <xref:System.Security.Permissions.StrongNameIdentityPermission> 對於完全信任組件沒有任何影響。 您必須自行檢查強式名稱是否相符。<br /><br /> 如果 `y` 和 `n` 都沒有指定，則此選項會顯示目前設定。 預設為 `y`。 **注意：** 在 64 位元電腦上，您必須在 Sn.exe 的 32 位元和 64 位元執行個體中設定此參數。|  
|**-q**[**uiet**]|指定無訊息模式，不顯示成功訊息。|  
|**-R**[**a**] *assembly* *infile*|以 *infile* 中的金鑰組重新簽署先前已簽署或延遲簽署的組件。<br /><br /> 如果使用了 **-Ra**，則會針對組件中的所有檔案重新計算雜湊。|  
|**-Rc**[**a**] *assembly container*|以 *container* 中的金鑰組重新簽署先前已簽署或延遲簽署的組件。<br /><br /> 如果使用了 **-Rca**，則會針對組件中的所有檔案重新計算雜湊。|  
|**-Rh** *assembly*|針對組件中的所有檔案重新計算雜湊。|  
|**-t**[**p**] *infile*|顯示存放在 *infile* 中公開金鑰的語彙基元。 *infile* 的內容必須是先前使用 **-p** 從金鑰組檔案中產生的公開金鑰。  請不要使用 **-t[p]** 選項，直接從金鑰組檔案中擷取語彙基元。<br /><br /> Sn.exe 是使用公開金鑰中的雜湊函式來計算語彙基元。 為了節省空間，通用語言執行平台在將相依性記錄到具有強式名稱的組件時，會將公開金鑰語彙基元存放到資訊清單中，做為其他組件參考的一部分。 除了語彙基元之外，**-Tp** 選項還會顯示公開金鑰。 如果 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性已套用至組件，則語彙基元代表識別金鑰，然後會顯示雜湊演算法和識別金鑰的名稱。<br /><br /> 請注意，此選項不會驗證組件簽章，且不應該用來進行信任決策。  此選項只會顯示未經處理的公開金鑰語彙基元資料。|  
|**-T**[**p**] *assembly*|顯示 *assembly.* 的公開金鑰語彙基元。 *assembly* 必須是含有組件資訊清單的檔案名稱。<br /><br /> Sn.exe 是使用公開金鑰中的雜湊函式來計算語彙基元。 為了節省空間，執行階段在將相依性記錄到具有強式名稱的組件時，會將公開金鑰語彙基元存放到資訊清單中，做為其他組件參考的一部分。 除了語彙基元之外，**-Tp** 選項還會顯示公開金鑰。 如果 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性已套用至組件，則語彙基元代表識別金鑰，然後會顯示雜湊演算法和識別金鑰的名稱。<br /><br /> 請注意，此選項不會驗證組件簽章，且不應該用來進行信任決策。  此選項只會顯示未經處理的公開金鑰語彙基元資料。|  
|`-TS` `assembly` `infile`|以 `assembly` 中的金鑰組，對已簽署或部分簽署的 `infile` 進行簽署測試。|  
|-`TSc` `assembly` `container`|以金鑰容器 `assembly` 中的金鑰組，對已簽署或部分簽署的 `container` 進行簽署測試。|  
|**-v** *assembly*|驗證 *assembly* 中的強式名稱，此處的 *assembly* 是含有組件資訊清單的檔案名稱。|  
|**-vf**  *assembly*|驗證 *assembly.* 中的強式名稱。 與 **-v** 選項不同的是，即使使用 **-Vr** 選項停用 **-vf**，它還是會強制執行驗證。|  
|**-Vk**  *regfile.reg* *assembly* [*userlist*] [*infile*]|建立註冊項目 (.reg) 檔案，您可以使用該檔案註冊要略過驗證的指定組件。 適用於 **-Vr** 選項的組件命名規則同樣適用於 **–Vk**。 如需 *userlist* 和 *infile* 選項的詳細資訊，請參閱 **–Vr** 選項。|  
|**-Vl**|列出這部電腦上強式名稱驗證的目前設定。|  
|**-Vr**  *assembly* [*userlist*] [*infile*]|註冊要略過驗證的 *assembly*。 或者，您可以指定要套用略過驗證的逗號分隔使用者名稱清單。 如果指定 *infile*，驗證會保持啟用狀態，不過 *infile* 中的公開金鑰會在驗證作業中使用。 您可以採用 *\*, strongname* 格式指定 *assembly*，以便註冊所有具有指定強式名稱的組件。 *strongname* 請指定十六位數的字串，表示公開金鑰的語彙基元形式。 若要顯示公開金鑰語彙基元，請參閱 **-t** 和 **-T** 選項。 **注意：** 此選項僅供開發期間使用。 將組件加入至略過驗證清單會使安全性變弱。 具有惡意的組件可能使用加入至略過驗證清單之組件的完全指定組件名稱 (組件名稱、版本、文化特性和公開金鑰語彙基元)，以偽裝其識別 (Identity)。 這會使具有惡意的組件也略過驗證。|  
|||  
|**-Vu**  *assembly*|移除要略過驗證之 *assembly* 的註冊。 適用於 **-Vr** 的組件命名規則同樣適用於 **-Vu**。|  
|**-Vx**|移除所有略過驗證的項目。|  
|**-?**|顯示工具的命令語法和選項。|  
  
> [!NOTE]
>  所有 Sn.exe 選項都區分大小寫，而且必須完全依照顯示的方式輸入，工具才能夠辨認。  
  
## <a name="remarks"></a>備註  
 **-R** 和 **–Rc** 選項搭配已延遲簽署的組件時非常實用。 在此情節中，在編譯時期只會設定公開金鑰，並且在稍後知道私密金鑰時才進行簽署。  
  
> [!NOTE]
>  若為寫入像是登錄這類受保護資源的參數 (例如，–**Vr)**，請以系統管理員身分執行 SN.exe。  
  
強式名稱工具假設會使用 `AT_SIGNATURE` 演算法識別碼來產生公開/私密金鑰組。 使用 `AT_KEYEXCHANGE` 演算法產生的公開/私密金鑰組會產生錯誤。 

## <a name="examples"></a>範例  
 下列命令會建立新的隨機金鑰組，並將它存放到 `keyPair.snk` 中。  
  
```  
sn -k keyPair.snk  
```  
  
 下列命令會將金鑰儲存在強式名稱 CSP 中 `keyPair.snk` 容器的 `MyContainer` 中。  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 下列命令會從 `keyPair.snk` 擷取公開金鑰，並將它存放到 `publicKey.snk` 中。  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 下列命令會顯示 `publicKey.snk` 中所包含之公開金鑰和公開金鑰的語彙基元。  
  
```  
sn -tp publicKey.snk  
```  
  
 下列命令會驗證組件 `MyAsm.dll`。  
  
```  
sn -v MyAsm.dll  
```  
  
 下列命令會從預設的 CSP 刪除 `MyContainer`。  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [Al.exe (組件連結器)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
