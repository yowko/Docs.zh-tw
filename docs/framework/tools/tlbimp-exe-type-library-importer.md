---
title: "Tlbimp.exe (類型程式庫匯入工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type libraries [.NET Framework], importing
- importing type library
- Tlbimp.exe
- type definition conversion
- Type Library Importer
- type libraries
- converting type definitions
ms.assetid: ec0a8d63-11b3-4acd-b398-da1e37e97382
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e6b98d03988c5eb747fb3a4c766c98f477a3b5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (類型程式庫匯入工具)
類型程式庫匯入工具會將 COM 類型程式庫中找到的類型定義轉換為通用語言執行平台組件中的對等定義。 Tlbimp.exe 的輸出是二進位檔案 (組件)，它包含原始類型程式庫中所定義類型的執行階段中繼資料。 您可以使用像是 [Ildasm.exe](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 這類工具來檢查這個檔案。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
tlbimp tlbFile [options]  
```  
  
#### <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|*tlbFile*|任何包含 COM 類型程式庫之檔案的名稱。|  
  
|選項|描述|  
|------------|-----------------|  
|**/asmversion:** *versionnumber*|指定要產生之組件的版本號碼。 以 *major.minor.build.revision* 格式指定 *versionnumber*。|  
|**/company:** `companyinformation`|將公司資訊加入至輸出組件。|  
|**/copyright:** `copyrightinformation`|將著作權資訊加入至輸出組件。 這項資訊可以在組件的 [檔案屬性] 對話方塊中進行檢視。|  
|**/delaysign**|指定由 Tlbimp.exe 使用延遲簽署以強式名稱簽署產生的組件。 您必須指定這個選項來配合 **/keycontainer:**、**/keyfile:** 或 **/publickey:** 選項。 如需延遲簽署程序的詳細資訊，請參閱[延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)。|  
|**/help**|顯示工具的命令語法和選項。|  
|**/keycontainer:** *containername*|使用 *containername* 所指定之金鑰容器中的公開/私密金鑰組，以強式名稱簽署產生的組件。|  
|**/keyfile:** *filename*|使用 *filename* 中發行者的正式公開/私密金鑰組，以強式名稱簽署產生的組件。|  
|**/machine:** `machinetype`|建立以所指定電腦類型 (微處理器) 為目標的組件。 支援的電腦類型：x86、x64、Itanium 和 Agnostic。|  
|**/namespace:** *namespace*|指定要在其中產生組件的命名空間。|  
|**/noclassmembers**|防止 Tlbimp.exe 將成員加入至類別。 這樣做可避免可能發生的 <xref:System.TypeLoadException>。|  
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|  
|**/out:** *filename*|指定要在其中寫入中繼資料定義的輸出檔、組件及命名空間名稱。 如果類型程式庫指定可明確控制組件命名空間的介面定義語言 (IDL) 自訂屬性，則 **/out** 選項不會影響組件的命名空間。 如果未指定這個選項，Tlbimp.exe 會將中繼資料寫入與輸入檔所定義之實際類型程式庫同名的檔案中，並指派 .dll 做為其副檔名。 如果輸出檔與輸入檔同名，則工具將會產生錯誤以防止覆寫類型程式庫。|  
|**/primary**|為指定的類型程式庫產生主要 Interop 組件。 組件中會加入資訊，指出類型程式庫的發行者產生該組件。 藉由指定主要 Interop 組件，就可以區別發行者的組件與使用 Tlbimp.exe 從類型程式庫建立的任何其他組件。 如果您是類型程式庫的發行者，而且您要使用 Tlbimp.exe 匯入該類型程式庫，則應該只使用 **/primary** 選項。 請注意，您必須以[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)簽署主要 Interop 組件。 如需詳細資訊，請參閱[主要 Interop 組件](http://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080)。|  
|**/product:** `productinformation`|將產品資訊加入至輸出組件。 這項資訊可以在組件的 [檔案屬性] 對話方塊中進行檢視。|  
|**/productversion:** `productversioninformation`|將產品版本資訊加入至輸出組件。 沒有格式限制。 這項資訊可以在組件的 [檔案屬性] 對話方塊中進行檢視。|  
|**/publickey:** *filename*|指定包含公開金鑰的檔案，用來簽署產生的組件。 如果您指定 **/keyfile:** 或 **/keycontainer:** 選項而不是 **/publickey:**，Tlbimp.exe 將會從 **/keyfile:** 或 **/keycontainer:** 提供的公開/私密金鑰組產生公開金鑰。 **/publickey:** 選項支援測試金鑰和延遲簽署情節。 檔案會採用 Sn.exe 產生的格式。 如需詳細資訊，請參閱[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 中 Sn.exe 的 **-p** 選項。|  
|**/reference:** *filename*|指定組件檔案，用來解析在目前類型程式庫外定義之類型的參考。 如果您未指定 **/reference** 選項，Tlbimp.exe 會自動以遞迴方式匯入所匯入之類型程式庫參考的任何外部類型程式庫。 如果您指定 **/reference** 選項，則工具在匯入其他類型程式庫之前，會先嘗試解析所參考組件中的外部類型。|  
|**/silence:** `warningnumber`|隱藏顯示指定的警告。 此選項無法搭配 **/silent** 使用。|  
|**/silent**|隱藏顯示成功訊息。 此選項無法搭配**/silence** 使用。|  
|**/strictref**|如果工具無法解析目前組件中、以 **/reference** 選項指定的組件中，或是已登錄的主要 Interop 組件 (PIA) 中的所有參考，則不匯入類型程式庫。|  
|**/strictref:nopia**|與 **/strictref** 相同，但是會忽略 PIA。|  
|**/sysarray**|指定由這個工具匯入 COM 樣式的 SafeArray 作為 Managed <xref:System.Array> 類型。|  
|**/tlbreference:** *filename*|指定用來解析類型程式庫參考的類型程式庫檔案，而不需要查閱登錄。<br /><br /> 請注意，這個選項將不會載入某些較舊的類型程式庫格式。  但是，您仍然可以透過登錄或目前的目錄，以隱含方式載入較舊的類型程式庫格式。|  
|**/trademark:** `trademarkinformation`|將商標資訊加入至輸出組件。 這項資訊可以在組件的 [檔案屬性] 對話方塊中進行檢視。|  
|**/transform:** *transformname*|依照 *transformname* 參數所指定，轉換中繼資料。<br /><br /> 為 *transformname* 參數指定 **dispret**，以便將分配介面 (Dispinterface) 上方法的 [out, retval] 參數轉換為傳回值。<br /><br /> 如需有關這個選項的詳細資訊，請參閱本主題後段的範例。|  
|**/unsafe**|不經過 .NET Framework 安全性檢查即產生介面。 呼叫以這種方式公開的方法可能會造成安全性風險。 除非您很清楚公開這類程式碼的風險，否則不應該使用這個選項。|  
|**/verbose**|指定詳細資訊模式，顯示有關匯入之類型程式庫的其他資訊。|  
|**/VariantBoolFieldToBool**|將結構中的 `VARIANT_BOOL` 欄位轉換為 <xref:System.Boolean>。|  
|**/?**|顯示工具的命令語法和選項。|  
  
> [!NOTE]
>  Tlbimp.exe 的命令列選項不區分大小寫，而且可以依任何順序提供。 您只需要指定足夠的選項來唯一識別它。 因此，**/n** 相當於 **/nologo**，而 **/ou:** *outfile.dll* 相當於 **/out:** *outfile.dll*。  
  
## <a name="remarks"></a>備註  
 Tlbimp.exe 會一次執行整個類型程式庫的轉換。 您無法使用這個工具針對單一類型程式庫中定義的類型子集產生類型資訊。  
  
 將[強式名稱](../../../docs/framework/app-domains/strong-named-assemblies.md)指派給組件的功能通常十分實用，甚至是必要的。 因此，Tlbimp.exe 包含了提供產生以強式名稱命名之組件所需資訊的選項。 **/keyfile:** 和 **/keycontainer:** 這兩個選項都會以強式名稱簽署組件。 所以邏輯上來說，一次只需要提供其中一個選項。  
  
 您可以多次使用 **/reference** 選項指定多個參考組件。  
  
 從包含多個類型程式庫的模組匯入類型程式庫時，可以選擇性地將資源 ID 附加至類型程式庫檔案。 只有在這個檔案是位於目前的目錄中，或者您指定了完整路徑時，Tlbimp.exe 才能夠找到這個檔案。 請參閱本主題稍後的範例。  
  
## <a name="examples"></a>範例  
 下列命令會產生與 `myTest.tlb` 中所找到的類型程式庫同名且副檔名為 .dll 的組件。  
  
```  
tlbimp myTest.tlb   
```  
  
 下列命令會產生名稱為 `myTest.dll` 的組件。  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 下列命令會產生與 `MyModule.dll\1` 所指定類型程式庫同名且副檔名為 .dll 的組件。 `MyModule.dll\1` 必須位於目前的目錄中。  
  
```  
tlbimp MyModule.dll\1  
```  
  
 下列命令會針對 `myTestLib.dll` 類型程式庫產生名稱為 `TestLib.dll` 的組件。 **/transform:dispret** 選項會將類型程式庫中分配介面上之方法的所有 [out, retval] 參數，轉換為 Managed 程式庫中的傳回值。  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 前一個範例中的 `TestLib.dll` 類型程式庫包括名為 `SomeMethod` 的分配介面方法，該方法會傳回 void 並具有 [out, retval] 參數。 以下程式碼是 `SomeMethod` 中 `TestLib.dll` 的輸入類型程式庫方法簽章。  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 指定 **/transform:dispret** 選項會使 Tlbimp.exe 將 `SomeMethod` 的 `[out, retval]` 參數轉換為 `bool` 傳回值。 以下是在指定 **/transform:dispret** 選項時，Tlbimp.exe 為 `myTestLib.dll` Managed 程式庫中的 `SomeMethod` 所產生的方法簽章。  
  
```csharp  
bool SomeMethod();  
```  
  
 如果您使用 Tlbimp.exe 為 `TestLib.dll` 產生 Managed 程式庫，而未指定 **/transform:dispret**，則工具會在 `myTestLib.dll` Managed 程式庫中為 `SomeMethod` 產生下列方法簽章。  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [Tlbexp.exe (類型程式庫匯出工具)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [匯入類型程式庫做為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [型別程式庫至組件轉換的摘要](http://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [強式名稱的組件](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [將型別程式庫匯入 Interop 組件的屬性](http://msdn.microsoft.com/library/81e587b8-393f-43e1-9add-c4b05e65cbfd)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
