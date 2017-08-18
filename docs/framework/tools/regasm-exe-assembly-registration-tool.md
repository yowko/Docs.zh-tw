---
title: "Regasm.exe (組件登錄工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
caps.latest.revision: 20
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 553b7725d2e0fe8fc197805d8e4b444567c33040
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (組件登錄工具)
組件註冊工具會讀取組件內的中繼資料，並將必要的項目加入至登錄，這樣可讓 COM 用戶端順利地建立 .NET Framework 類別。 註冊類別之後，任何 COM 用戶端都可以將它當做 COM 類別使用。 類別只會在安裝組件時註冊一次。 在實際註冊類別之後，才能從 COM 建立組件內類別的執行個體。  
  
 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
regasm assemblyFile [options]  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|說明|  
|---------------|-----------------|  
|*assemblyFile*|要向 COM 註冊的組件。|  
  
|選項|說明|  
|------------|-----------------|  
|**/codebase**|在登錄中建立一個程式碼基底項目。 程式碼基底項目會指定未安裝於全域組件快取中之組件的檔案路徑。 如果您將接著安裝要在全域組件快取中註冊的組件，則不應該指定這個選項。 您使用 **/codebase** 選項指定的 *assemblyFile* 引數必須是[強式名稱組件](../../../docs/framework/app-domains/strong-named-assemblies.md)。|  
|**/registered**|指定這個工具只會參考已註冊的類型程式庫。|  
|**/asmpath:directory**|指定包含組件參考的目錄。 必須與 **/regfile** 選項一起使用。|  
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|  
|**/regfile** [**:** *regFile*]|產生組件的指定 .reg 檔，其中包含所需的登錄項目。 指定這個選項並不會變更登錄。 這個選項不可與 **/u** 或 **/tlb** 選項一起使用。|  
|**/silent** 或 **/s**|隱藏顯示成功訊息。|  
|**/tlb** [**:** *typeLibFile*]|從指定的組件中產生類型程式庫，其中包含組件內所定義之可存取類型的定義。|  
|**/unregister** 或 **/u**|移除註冊 *assemblyFile* 中所找到的可建立類別。 省略這個選項會造成 Regasm.exe 註冊組件中可建立的類別。|  
|**/verbose**|指定詳細資訊模式，與 **/tlb** 選項一起指定時，顯示需要產生型別程式庫之任何參考組件的清單。|  
|**/?** 或 **/help**|顯示工具的命令語法和選項。|  
  
> [!NOTE]
>  Regasm.exe 命令列選項不區分大小寫。 您只需要提供足夠的選項資訊，就可唯一識別該選項。 例如，**/n** 相當於 **/nologo**，且 **/t:** *outfile.tlb* 相當於 **/tlb:** *outfile.tlb*。  
  
## <a name="remarks"></a>備註  
 您可以使用 **/regfile** 選項產生包含登錄項目的 .reg 檔，而不是直接變更登錄。 您可以使用登錄編輯程式工具 (Regedit.exe) 匯入 .reg 檔，藉此更新電腦上的登錄。 請注意，.reg 檔並不包含任何可以藉由使用者定義的註冊功能處理的登錄更新。  請注意，**/regfile** 選項只會發出 Managed 類別的登錄項目。  這個選項不會發出 `TypeLibID` 或 `InterfaceID` 的項目。  
  
 當您指定 **/tlb** 選項時，Regasm.exe 會產生及註冊型別程式庫，描述組件中找到的類型。 Regasm.exe 會將產生的類型程式庫放入目前的工作目錄中，或是為輸出檔指定的目錄中。 為參考其他組件的組件產生類型程式庫可能導致一次產生多個類型程式庫。 您可以使用類型程式庫提供類型資訊給 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 這類開發工具。 如果您要註冊的組件是由型別程式庫匯入工具 ([Tlbimp.exe](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)) 所產生，則不應該使用 **/tlb** 選項。 您無法從原本自類型程式庫匯入的組件匯出類型程式庫。 使用 **/tlb** 選項與使用類型程式庫匯出工具 ([Tlbexp.exe](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)) 和 Regasm.exe 的效果相同，但是有一點除外，就是 Tlbexp.exe 不會註冊本身所產生的類型資料庫。  如果您使用 **/tlb** 選項註冊型別程式庫，就可以使用 **/tlb** 選項搭配 **/unregister** 選項將型別程式庫的註冊移除。 這兩個選項一起使用時，將會移除類型程式庫和介面項目的註冊，因而大幅清除登錄。  
  
 當您註冊 COM 要使用的組件時，Regasm.exe 會將項目加入至本機電腦上的登錄。 更精確地說，它會建立與版本相關的登錄機碼，允許相同組件的多個版本在電腦上並存執行。 第一次註冊組件時，系統會針對組件建立一個最上層機碼，並針對這個特定版本建立一個唯一子機碼。 每次您註冊新的組件版本時，Regasm.exe 就會為這個新的版本建立一個子機碼。  
  
 例如，假設您註冊 Managed 元件 myComp.dll 1.0.0.0 版以供 COM 使用。 稍後您又註冊 myComp.dll 2.0.0.0 版。 您決定讓電腦上的所有 COM 用戶端應用程式都使用 myComp.dll 2.0.0.0 版，並決定移除 myComponent.dll 1.0.0.0 版的註冊。 這項登錄配置可讓您移除 myComp.dll 1.0.0.0 版的註冊，因為只會移除 1.0.0.0 版的子機碼。  
  
 使用 Regasm.exe 註冊組件之後，您可以將它安裝在[全域組件快取](../../../docs/framework/app-domains/gac.md)中，以便可以從任何 COM 用戶端將它啟用。 如果組件將只會由單一應用程式啟用，您可以將它放置到該應用程式的目錄中。  
  
## <a name="examples"></a>範例  
 下列命令會註冊所有包含在 `myTest.dll` 中的公用類別。  
  
```  
regasm myTest.dll  
```  
  
 下列命令會產生 `myTest.reg` 檔案，該檔案中包含所有必要的登錄項目。 這個命令不會更新登錄。  
  
```  
regasm myTest.dll /regfile:myTest.reg  
```  
  
 下列命令會註冊包含在 `myTest.dll` 檔中的所有公用類別，並且產生和註冊 `myTest.tlb` 類型程式庫，其中包含所有在 `myTest.dll` 中定義之公用類型的定義。  
  
```  
regasm myTest.dll /tlb:myTest.tlb  
```  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../../docs/framework/tools/index.md)   
 [Tlbexp.exe (類型程式庫匯出工具)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)   
 [Tlbimp.exe (型別程式庫匯入工具)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)   
 [向 COM 註冊組件](../../../docs/framework/interop/registering-assemblies-with-com.md)   
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

