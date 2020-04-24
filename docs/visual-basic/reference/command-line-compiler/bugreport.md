---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 02d84bceb0242988c70889ddd5d3dc7530f6e808
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793539"
---
# <a name="-bugreport"></a>-bugreport

建立檔案，您可以在提出 bug 報告時使用。

## <a name="syntax"></a>語法

```console
-bugreport:file
```

## <a name="arguments"></a>引數

|詞彙|定義|
|---|---|
|`file`|必要。 將包含 bug 報告的檔案名。 如果名稱包含空格，請用引號（""）括住檔案名。|

## <a name="remarks"></a>備註

下列資訊會新增至`file`：

- 編譯中所有原始程式碼檔案的複本。

- 編譯中使用的編譯器選項清單。

- 您的編譯器、通用語言執行時間和作業系統的版本資訊。

- 編譯器輸出 (如果有的話)。

- 問題的描述，會提示您。

- 您認為問題的說明應如何修正，而系統會提示您。

由於中`file`包含所有原始程式碼檔的複本，因此您可能會想要在最短的可能程式中重現（疑似）程式碼缺失。

> [!IMPORTANT]
> `-bugreport`選項會產生包含潛在敏感性資訊的檔案。 這包括目前時間、編譯器版本、.NET Framework 版本、作業系統版本、使用者名稱、編譯器執行時所使用的命令列引數、所有原始程式碼，以及任何參考元件的二進位格式。 藉由在 web.config 檔案中指定命令列選項來進行 ASP.NET 應用程式的伺服器端編譯，即可存取此選項。 若要避免這種情況，請修改 Machine.config 檔案，讓使用者不允許在伺服器上編譯。

如果搭配`-errorreport:prompt`、 `-errorreport:queue`或`-errorreport:send`使用此選項，且您的應用程式發生編譯器內部錯誤，則會將中`file`的資訊傳送給 Microsoft Corporation。 這項資訊可協助 Microsoft 工程師找出錯誤的原因，並可協助改善下一版的 Visual Basic。 根據預設，不會將任何資訊傳送至 Microsoft。 不過，當您使用`-errorreport:queue`來編譯應用程式時（預設會啟用），應用程式會收集其錯誤報表。 然後，在電腦的系統管理員登入時，錯誤報表系統會顯示一個快顯視窗，可讓系統管理員將登入後發生的任何錯誤報表轉寄給 Microsoft。

> [!NOTE]
> 此`-bugreport`選項無法在 Visual Studio 開發環境中使用;只有當您從命令列編譯時，才可以使用它。

## <a name="example"></a>範例

下列範例會編譯*T2 .vb* ，並將所有 bug 報告資訊放在檔案*問題 .txt*中。

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-debug （Visual Basic）](debug.md)
- [-errorreport](errorreport.md)
- [編譯命令列範例](sample-compilation-command-lines.md)
- [securityPolicy 的 trustLevel 項目 (ASP.NET 設定結構描述)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
