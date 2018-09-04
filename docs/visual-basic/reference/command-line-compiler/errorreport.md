---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d093b8ce4413a375e79eec239be37e83ac674d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509669"
---
# <a name="-errorreport"></a>-errorreport

指定 Visual Basic 編譯器報告編譯器內部錯誤的方式。

## <a name="syntax"></a>語法

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a>備註

此選項會提供便利的方式來將 Visual Basic 編譯器內部錯誤 (ICE) 回報到 Microsoft 的 Visual Basic 小組。 根據預設，編譯器會將任何資訊傳送給 Microsoft。 不過，如果您真的遇到編譯器內部錯誤，此選項可讓您向 Microsoft 回報錯誤。 這項資訊可協助 Microsoft 工程師找出原因，而且可能有助於改善下一版的 Visual Basic。

傳送報表的使用者的能力取決於電腦和使用者原則權限。

下表摘要說明的效果`-errorreport`選項。

|選項|行為|
|---|---|
|`prompt`|發生編譯器內部錯誤時，對話方塊隨即出現，您可以檢視編譯器所收集的確切資料。 您可以判斷是否有任何錯誤報表中的機密資訊，並決定是否要將它傳送給 Microsoft。 如果您決定要傳送，而且電腦和使用者的原則設定允許，編譯器會將資料傳送給 Microsoft。|
|`queue`|佇列錯誤報告。 當您登入系統管理員權限時，您可以在上次登入報告任何失敗 （不會提示您傳送錯誤報告的頻率超過每隔三天一次）。 這是預設行為時`-errorreport`未指定選項。|
|`send`|如果發生編譯器內部錯誤，而且電腦和使用者的原則設定允許，編譯器會將資料傳送給 Microsoft。<br /><br /> 選項`-errorreport:send`會嘗試自動將錯誤資訊傳送給 Microsoft，如果已啟用 reporting [Windows 錯誤報告](/windows/desktop/wer/windows-error-reporting)系統設定。 |
|`none`|發生編譯器內部錯誤時，它將不會收集或傳送給 Microsoft。|

編譯器會將傳送資料，包括堆疊時的錯誤，通常包括一些原始程式碼。 如果`-errorreport`搭配[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，則會傳送整個原始程式檔。

這個選項最適合搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，因為它可讓 Microsoft 工程師更輕鬆地重現錯誤。

> [!NOTE]
> `-errorreport`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。

## <a name="example"></a>範例

下列程式碼會嘗試編譯`T2.vb`，和如果編譯器發生編譯器內部錯誤，它會提示您傳送錯誤報表給 Microsoft。

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
