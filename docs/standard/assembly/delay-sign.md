---
title: 延遲簽署元件
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: e7679520e246ab3eda03e6f0e0d092c7d09f1845
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991325"
---
# <a name="delay-sign-an-assembly"></a>延遲簽署元件

組織可能會有一組嚴密受防護的金鑰組，開發人員每日無法存取。 公開金鑰經常都可以使用，但只有少數人才能存取私密金鑰。 在以強式名稱開發組件時，每個參考強式名稱目標組件的組件都包含用來指定目標組件的強式名稱的公開金鑰語彙基元。 這需要可在開發程序期間使用公開金鑰。

您可以在組建階段使用延遲或部分簽署，以在可移植執行檔（PE）中保留強式名稱簽章的空間，但在稍後的階段（通常是在出貨元件之前）延遲實際的簽署。

若要延遲簽署元件：

1. 從將執行最終簽署的組織取得金鑰組的公開金鑰部分。 通常此金鑰的格式為 .snk 檔案，可以使用 Windows SDK 所提供的[強式名稱工具（sn.exe）](../../framework/tools/sn-exe-strong-name-tool.md)來建立 *。*

2. 使用來自 <xref:System.Reflection> 的兩個自訂屬性為組件的原始碼加上註解：

   - <xref:System.Reflection.AssemblyKeyFileAttribute>，它會將傳遞包含公開金鑰的檔案名稱，作為其建構函式的參數。

   - <xref:System.Reflection.AssemblyDelaySignAttribute>，它指出正在藉由傳遞 **true** 作為其建構函式的參數來使用延遲簽署。

   例如:

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. 編譯器會將公開金鑰插入到組件資訊清單，並在 PE 檔中保留完整強式名稱簽章的空間。 在建置組件時必須儲存真正的公開金鑰，以便參考這個組件的其他組件可以取得金鑰，儲存在它們自己的組件參考。

4. 因為組件沒有有效的強式名稱簽章，所以該簽章的驗證作業必須關閉。 您可以使用 **-Vr** 選項搭配強式名稱工具完成此作業。

     下列範例會關閉名為*myAssembly*之元件的驗證。

   ```console
   sn –Vr myAssembly.dll
   ```

   若要在您無法在執行強式名稱工具的平台上關閉驗證，例如 Advanced RISC Machine (ARM) 微處理器，請使用 **– Vk** 選項來建立登錄檔。 將登錄檔匯入到您要關閉驗證的電腦上的登錄。 下列範例將建立 `myAssembly.dll` 的登錄檔。

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   使用 **-Vr**或 **– Vk**選項時，您可以選擇性地包含用於測試金鑰簽署的 *.snk*檔案。

   > [!WARNING]
   > 請勿依賴強式名稱提供安全性。 強式名稱僅提供唯一識別。

   > [!NOTE]
   > 如果您在 64 位元電腦上，使用 Visual Studio 進行開發期間使用延遲簽署，並且編譯**任何 CPU** 的組件，您可能要套用 **-Vr** 選項兩次。 (在 Visual Studio 中，**任何 CPU** 是**平台目標**建置屬性的值，當您從命令列編譯時，它是預設值。)若要從命令列或從 [檔案管理器] 執行應用程式，請使用64位版本的[sn.exe （強式名稱工具）](../../framework/tools/sn-exe-strong-name-tool.md) ，將 **-Vr**選項套用至元件。 若要在設計階段將組件載入到 Visual Studio (例如，如果組件包含您應用程式中其他組件使用的元件)，請使用 32 位元版本的強式名稱工具。 這是因為當組件是從命令列執行時，just-in-time (JIT) 編譯器會將組件編譯為 64 位元原生程式碼，而當載入到設計階段環境時，編譯為 32 位元原生程式碼。

5. 稍後，通常就在傳送之前，您會將組件送出給貴組織的簽署授權單位，以便使用強式名稱工具的 **–R** 選項進行實際的強式名稱簽署。

   下列範例會使用*sgKey*金鑰組，以強式名稱簽署名為*myAssembly*的元件。

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>另請參閱

- [建立元件](create.md)
- [如何：建立公開/私密金鑰組](create-public-private-key-pair.md)
- [Sn.exe （強式名稱工具）](../../framework/tools/sn-exe-strong-name-tool.md)
- [具有元件的程式](program.md)
