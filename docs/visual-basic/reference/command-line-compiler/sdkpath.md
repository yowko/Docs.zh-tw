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
ms.openlocfilehash: 91f64756b2fbf14dc96550420cd936973e6bec87
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268289"
---
# <a name="-sdkpath"></a>-sdkpath
指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引數  
 `path`  
 包含 mscorlib.dll 和 Microsoft.VisualBasic.dll 編譯来使用的版本的目錄。 此路徑未驗證之前載入。 將目錄名稱括在引號 ("") 如果它包含空格。  
  
## <a name="remarks"></a>備註  
 此選項會告訴 Visual Basic 編譯器，從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。 `-sdkpath`選項設計來搭配[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。 .NET Compact Framework 會使用不同版本的支援程式庫，以避免使用的類型和裝置上找不到的語言功能。  
  
> [!NOTE]
>  `-sdkpath`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。 `-sdkpath` Visual Basic 裝置專案載入時，設定選項。  
  
 您可以指定編譯器應使用編譯 Visual Basic 執行階段程式庫參考`-vbruntime`編譯器選項。 如需詳細資訊，請參閱 < [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Myfile.vb`使用.NET Compact Framework 中，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中找到.NET Compact Framework 的 C 磁碟機上的預設安裝目錄。 一般而言，您會使用.NET Compact Framework 的最新版本。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
