---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 46cec7ac3cb78c4fc97e299535f9085eff6daeff
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004688"
---
# <a name="-sdkpath"></a>-sdkpath
指定 mscorlib.dll 和 Microsoft 的位置。  
  
## <a name="syntax"></a>語法  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引數  
 `path`  
 包含要用於編譯之 mscorlib.dll 和 node.js 版本的目錄。 此路徑要等到載入後才會驗證。 如果目錄名稱包含空格，請將其括在引號（""）中。  
  
## <a name="remarks"></a>備註  
 此選項會告訴 Visual Basic 編譯器從非預設位置載入 mscorlib.dll 和 Microsoft..。 @No__t-0 選項是設計來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)使用。 .NET Compact Framework 會使用這些支援程式庫的不同版本，以避免使用在裝置上找不到的類型和語言功能。  
  
> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。 載入 Visual Basic 裝置專案時，會設定 `-sdkpath` 選項。  
  
 您可以指定編譯器不需要使用 `-vbruntime` 編譯器選項來進行 Visual Basic 執行時間程式庫的參考編譯。 如需詳細資訊，請參閱[-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會使用在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到的 Mscorlib.dll 和 default.aspx 版本，搭配 .NET Compact Framework 來編譯 `Myfile.vb`。 一般來說，您會使用最新版本的 .NET Compact Framework。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
