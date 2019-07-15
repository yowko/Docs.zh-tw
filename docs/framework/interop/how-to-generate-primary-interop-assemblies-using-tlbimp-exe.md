---
title: 作法：使用 Tlbimp.exe 產生主要 Interop 組件
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b093f9bb633578cc0051cfca7b1362f8bf097d7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662452"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>作法：使用 Tlbimp.exe 產生主要 Interop 組件

有兩種方式可產生主要 Interop 組件：

- 使用 Windows 軟體開發套件 (SDK) 提供的[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)。

  產生主要 Interop 組件最直接的方法是使用[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)。 Tlbimp.exe 會提供下列保護措施：

  - 建立任何巢狀類型程式庫參考的新 Interop 組件之前，檢查是否有其他已註冊的主要 Interop 組件。

  - 如果您未指定容器或檔案名稱，來指定主要 Interop 組件的強式名稱，則無法發出主要 Interop 組件。

  - 如果您省略相依組件的參考，則無法發出主要 Interop 組件。

  - 如果您加入非主要 Interop 組件的相依組件的參考，則無法發出主要 Interop 組件。

- 使用與 Common Language Specification (CLS) 相容的語言，例如 C#，在原始程式碼中手動建立主要 Interop 組件。 無法使用類型程式庫時，這個方法就很有用。

您必須使用密碼編譯金鑰組將組件簽署為強式名稱。 如需詳細資料，請參閱[建立金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)。

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>使用 Tlbimp.exe 產生主要 Interop 組件

1. 在命令提示中，輸入：

    **tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*

    在這個命令中，*tlbfile* 是含有 COM 類型程式庫的檔案，*filename* 是含有金鑰組的容器或檔案名稱，而 *assemblyname* 則是要簽署為強式名稱的組件名稱。

主要 Interop 組件只能參考其他主要 Interop 組件。 如果您的組件參考來自協力廠商 COM 類型程式庫的類型，則您必須先從發行者取得主要 Interop 組件，才能產生主要 Interop 組件。 如果您是發行者，您必須先產生相依類別程式庫的主要 Interop 組件，才能產生參考的主要 Interop 組件。

安裝在目前的目錄時，無法探索與原始類型程式庫版本號碼不同的相依主要 Interop 組件。 您必須在 Windows 登錄中登錄相依的主要 Interop 組件，或使用 **/reference** 選項，以確定 Tlbimp.exe 能找到相依的 DLL。

您也可以包裝類型程式庫的多個版本。 如需相關指示，請參閱[如何：包裝型別程式庫的多個版本](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100))。

## <a name="example"></a>範例

下列範例會匯入 COM 類型程式庫  `LibUtil.tlb`，並使用金鑰檔案 `CompanyA.snk` 將組件 `LibUtil.dll` 簽署為強式名稱。 藉由略過特定命名空間名稱，此範例會產生預設的命名空間 `LibUtil`。

```
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

如需更具描述性的名稱 (使用 *VendorName*.*LibraryName* 命名指導方針)，下列範例會覆寫預設組件檔案名稱和命名空間名稱。

```
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

下列範例會匯入 `MyLib.tlb`，它參考 `CompanyA.LibUtil.dll` 並使用金鑰檔案 `CompanyB.snk` 將組件 `CompanyB.MyLib.dll` 簽署為強式名稱。 命名空間 `CompanyB.MyLib` 會覆寫預設命名空間名稱。

```
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a>另請參閱

- [如何：登錄主要 Interop 組件](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)
