---
title: 作法：登錄主要 Interop 組件
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e61ae55673cbf745ea4c637c5206efe41d8ab276
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946680"
---
# <a name="how-to-register-primary-interop-assemblies"></a>作法：登錄主要 Interop 組件

類別只能由 COM Interop 封送處理，並且一律會封送處理為介面。 在某些情況下，用來封送處理類別的介面就是所謂的類別介面。 如需以您選擇的介面來覆寫類別介面的資訊，請參閱 [COM 可呼叫包裝函式](../../standard/native-interop/com-callable-wrapper.md)。

 雖然想要從 .NET Framework 應用程式使用 COM 類型的任何開發人員都可以產生 Interop 組件，但這樣做會有問題。 每當開發人員匯入及簽署 COM 類型程式庫時，該開發人員會建立一組唯一類型，而這些類型會與另一個開發人員匯入及簽署的類型不相容。 這個類型不相容問題的解決方法可讓每個開發人員取得廠商提供及簽署的主要 Interop 組件。

 如果您打算向其他應用程式公開協力廠商 COM 類型，請一律使用與其定義之類型程式庫相同的發行者所提供的主要 Interop 組件。 除了提供保證的類型相容性，廠商也常常會自訂主要 Interop 組件來增強互通性。

 即使您不打算公開協力廠商 COM 類型，使用主要 Interop 組件也可以簡化與 COM 元件的互通工作。 不過，此策略不會針對廠商可能對主要 Interop 組件中定義之類型的變更進行隔離。 當您的應用程式需要這類隔離時，請產生您自己的 Interop 組件，而不要使用主要 Interop 組件。

 您必須先在開發電腦上註冊所有取得的主要 Interop 組件，才能使用 Visual Studio 來加以參考。 Visual Studio 會在您第一次從 COM 類型程式庫參考類型時，尋找並使用主要 Interop 組件。 如果 Visual Studio 找不到與類型程式庫相關聯的主要 Interop 組件，它會提示您取得該組件，或是提供您建立 Interop 組件的方式。 同樣地，[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 也會使用登錄來找出主要 Interop 組件。

 雖然除非您打算使用 Visual Studio，否則並不需要註冊主要 Interop 組件，但註冊有兩個優點：

- 已註冊的主要 Interop 組件會明確標示在原始類型程式庫的登錄機碼底下。 註冊是您在電腦上尋找主要 Interop 組件的最佳方式。

- 如果未來某些時候，您會使用 Visual Studio 來參考具有未註冊主要 Interop 組件的類型，就可以避免不小心產生及使用新的 Interop 組件。

使用[組件註冊工具 (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 來註冊主要 Interop 組件。

## <a name="to-register-a-primary-interop-assembly"></a>註冊主要 Interop 組件

1. 在命令提示中，輸入：

     **regasm** *assemblyname*

     在這個命令中，*assemblyname* 是已註冊組件的檔案名稱。 Regasm.exe 會在與原始類型程式庫相同的登錄機碼之下，加入主要 Interop 組件的項目。

## <a name="example"></a>範例
 下列範例會註冊 `CompanyA.UtilLib.dll` 主要 Interop 組件。

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a>另請參閱

- [使用主要 Interop 組件設計程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/baxfadst(v=vs.100))
- [找出主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y06sxw56(v=vs.100))
- [轉散發主要 Interop 組件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0dt2w20(v=vs.100))
