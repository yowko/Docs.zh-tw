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
ms.openlocfilehash: 18bf22861c1cbc3a37ef917b421491c2d01efba8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085109"
---
# <a name="-sdkpath"></a>-sdkpath

指定 mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。  
  
## <a name="syntax"></a>語法  
  
```console  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引數  

 `path`  
 包含 mscorlib.dll 版本的目錄，以及用於編譯的 Microsoft.VisualBasic.dll。 在載入之前，不會驗證此路徑。 以引號括住目錄名稱 ( "" ) 如果它包含空格。  
  
## <a name="remarks"></a>備註  

 此選項會指示 Visual Basic 編譯器從非預設位置載入 mscorlib.dll 和 Microsoft.VisualBasic.dll 檔案。 此 `-sdkpath` 選項的設計目的是要搭配 [-netcf](netcf.md)使用。 .NET Compact Framework 使用這些支援程式庫的不同版本，以避免使用在裝置上找不到的類型和語言功能。  
  
> [!NOTE]
> `-sdkpath`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。 `-sdkpath`載入 Visual Basic 裝置專案時，會設定此選項。  
  
 您可以使用編譯器選項，指定編譯器不需要參考 Visual Basic 執行時間程式庫 `-vbruntime` 。 如需詳細資訊，請參閱 [-vbruntime](vbruntime.md)。  
  
## <a name="example"></a>範例  

 下列程式碼會 `Myfile.vb` 使用 .NET Compact Framework，並使用在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本進行編譯。 一般來說，您會使用最新版本的 .NET Compact Framework。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [-netcf](netcf.md)
- [-vbruntime](vbruntime.md)
