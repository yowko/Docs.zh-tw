---
title: XML 序列化程式產生器工具 (Sgen.exe)
description: XML 序列化程式產生器會針對元件中的類型建立 XML 序列化元件，以改善 XmlSerializer 的啟動效能。
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: b6d9406ca6a69f7bdff3129b55c89dd5d1589d3f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288936"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML 序列化程式產生器工具 (Sgen.exe)

XML 序列化程式產生器會針對指定元件中的類型建立 XML 序列化元件。 序列化元件會在序列化或還原序列化 <xref:System.Xml.Serialization.XmlSerializer> 指定類型的物件時，改善的啟動效能。
  
## <a name="syntax"></a>語法

從命令列執行工具。
  
```console  
sgen [options]  
```
  
> [!TIP]
> 若要讓 .NET Framework 工具正常運作，您必須 `Path` `Include` 正確地設定、和 `Lib` 環境變數。 藉由執行 SDKVars （位於 \V2.0\Bin 目錄中）來設定這些環境變數 \<SDK> 。 SDKVars.bat 必須在每一個命令提示字元中執行。
  
## <a name="parameters"></a>參數  
  
|選項|描述|  
|------------|-----------------|  
|**/a \[ 元件 s) \] ：**_filename_|為組件中包含的所有類型或 *filename* 所指定的可執行檔產生序列化程式碼。 只能提供一個檔名。 如果重複使用這個引數，則會使用最後一個檔名。|  
|**/c \[ 譯器 \] ：**_選項_|指定要傳遞至 C# 編譯器的選項。 所有 csc.exe 選項都受到支援，可以傳遞至編譯器。 這個選項可以用來指定組件必須經過簽署，並指定金鑰檔。|  
|**/d \[ 偵錯\]**|產生可以與偵錯工具搭配使用的影像。|  
|**/f \[ orce\]**|強制覆寫現有的同名組件。 預設值為 **false**。|  
|**/help 或/？**|顯示工具的命令語法和選項。|  
|**/k \[ 保留\]**|將產生的原始程式檔 (Source File) 和其他暫存檔案編譯成序列化組件之後，隱藏刪除這些檔案的動作。 這個選項可以用來判斷工具是否正在為特定的型別產生序列化程式碼。|  
|**/n \[ ologo\]**|隱藏顯示 Microsoft 程式啟始資訊。|  
|**/o \[ \] 內容：**_路徑_|指定要在其中儲存所產生之組件的目錄。 **注意：** 產生的組件名稱是由輸入組件的名稱加上 "xmlSerializers.dll" 所組成。|  
|**/p \[ roxytypes\]**|只為 XML Web 服務 Proxy 型別產生序列化程式碼。|  
|**/r \[ eference \] ：**_assemblyfiles_|指定要求 XML 序列化的型別所參考的組件。 這個選項接受以逗號分隔多個組件檔案。|  
|**/s \[ ilent\]**|隱藏顯示成功訊息。|  
|**/t \[ 輸入 \] ：**_類型_|只為指定的型別產生序列化程式碼。|  
|**/v \[ erbose\]**|顯示詳細資訊輸出以供偵錯。 此選項會列出無法使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化之目標組件中的型別。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 如果未使用 XML 序列化程式產生器，則每當應用程式執行時，<xref:System.Xml.Serialization.XmlSerializer> 便會為每個型別產生序列化程式碼和序列化組件。 若要改善 XML 序列化啟動的效能，請使用 Sgen 工具來預先產生這些元件。 然後，這些組件便可以與應用程式一起部署。  
  
 XML 序列化程式產生器也可以改善用戶端使用 XML Web Service Proxy 與伺服器進行通訊的效能，因為在第一次載入型別時，序列化處理序並不會影響到效能。  
  
 這些產生的組件無法在 Web 服務的伺服器端上使用。 這個工具只能在 Web 服務用戶端和手動序列化案例中使用。  
  
 如果含有要序列化之型別的組件名稱為 MyType.dll，關聯的序列化組件名稱就會是 MyType.XmlSerializers.dll。  
  
## <a name="examples"></a>範例  
 下列命令會建立名為 Data.XmlSerializers.dll 的組件，用以序列化 Data.dll 組件中所包含的所有型別。  
  
```console  
sgen Data.dll
```  
  
 Data.XmlSerializers.dll 組件可以從程式碼參考，而該程式碼必須序列化及還原序列化 Data.dll 中的型別。  
  
## <a name="see-also"></a>另請參閱

- [工具](../../framework/tools/index.md)
- [命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)
