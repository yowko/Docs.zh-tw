---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 4b468b8ee4301693312e9545396f2b9f495f75d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550907"
---
# <a name="-bugreport"></a>-bugreport

建立您在提出錯誤報表時可以使用的檔案。

## <a name="syntax"></a>語法

```console
-bugreport:file
```

## <a name="arguments"></a>引數

|詞彙|定義|
|---|---|
|`file`|必要。 將包含 bug 報告的檔案名。 以引號括住檔案名 ( "" ) 如果名稱包含空格。|

## <a name="remarks"></a>備註

下列資訊會加入至 `file` ：

- 編譯中所有原始程式碼檔的複本。

- 編譯中所使用之編譯器選項的清單。

- 編譯器、common language runtime 和作業系統的版本資訊。

- 編譯器輸出 (如果有的話)。

- 系統提示您的問題描述。

- 您應該如何解決問題的說明，將會提示您。

由於中包含所有原始程式碼檔的複本 `file` ，因此您可能會想要在最短的程式中重現 (疑似) 程式碼缺失。

> [!IMPORTANT]
> `-bugreport`選項會產生包含潛在敏感資訊的檔案。 這包括目前的時間、編譯器版本、.NET Framework 版本、作業系統版本、使用者名稱、編譯器執行時所使用的命令列引數、所有原始程式碼，以及任何參考元件的二進位格式。 您可以藉由在 ASP.NET 應用程式的伺服器端編譯 Web.config 檔案中指定命令列選項，來存取這個選項。 若要避免這種情況，請修改 Machine.config 檔案，以禁止使用者在伺服器上進行編譯。

如果這個選項與 `-errorreport:prompt` 、或搭配使用 `-errorreport:queue` `-errorreport:send` ，而且您的應用程式發生編譯器內部錯誤，則中的資訊 `file` 會傳送至 Microsoft Corporation。 這項資訊可協助 Microsoft 工程師找出錯誤的原因，並可協助改善下一版的 Visual Basic。 依預設，不會將任何資訊傳送給 Microsoft。 但是，當您使用來編譯應用程式時， `-errorreport:queue` 預設會啟用此應用程式，而應用程式會收集其錯誤報表。 然後，當電腦的系統管理員登入時，錯誤報表系統就會顯示一個快顯視窗，讓系統管理員將登入之後發生的任何錯誤報表轉寄給 Microsoft。

> [!NOTE]
> `-bugreport`選項無法在 Visual Studio 開發環境中使用; 只有當您從命令列編譯時，才能使用此選項。

## <a name="example"></a>範例

下列範例會編譯 *T2* ，並將所有 bug 報告資訊放入 *Problem.txt*的檔案中。

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-debug (Visual Basic) ](debug.md)
- [-errorreport](errorreport.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [securityPolicy 的 trustLevel 項目 (ASP.NET 設定結構描述)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))
