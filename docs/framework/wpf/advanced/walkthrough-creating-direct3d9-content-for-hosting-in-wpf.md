---
title: 逐步解說：建立 Direct3D9 內容以裝載在 WPF 中
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 462220b526db90d3acfa90a28f9bfd56dbe813e2
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991402"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>逐步解說：建立 Direct3D9 內容以裝載在 WPF 中
本逐步解說示範如何建立適用于在 Windows Presentation Foundation （WPF）應用程式中裝載的 Direct3D9 內容。 如需有關在 WPF 應用程式中裝載 Direct3D9 內容的詳細資訊，請參閱[wpf 和 Direct3D9](wpf-and-direct3d9-interoperation.md)互通。

 在這個逐步解說中，您將執行下列工作：

- 建立 Direct3D9 專案。

- 設定 Direct3D9 專案以在 WPF 應用程式中進行裝載。

 當您完成時，您將會有一個 DLL，其中包含 WPF 應用程式中使用的 Direct3D9 內容。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- Visual Studio 2010。

- DirectX SDK 9 或更新版本。

## <a name="creating-the-direct3d9-project"></a>建立 Direct3D9 專案
 第一個步驟是建立及設定 Direct3D9 專案。

#### <a name="to-create-the-direct3d9-project"></a>若要建立 Direct3D9 專案

1. 在中C++建立名為`D3DContent`的新 Win32 專案。

     [Win32 應用程式精靈] 隨即開啟，並顯示 [歡迎使用] 畫面。

2. 按 [ **下一步**]。

     [應用程式設定] 畫面隨即出現。

3. 在 [**應用程式類型：** ] 區段中，選取 [ **DLL** ] 選項。

4. 按一下 [ **完成**]。

     會產生 D3DContent 專案。

5. 在方案總管中，以滑鼠右鍵按一下 D3DContent 專案，然後選取 [**屬性**]。

     [ **D3DContent 屬性頁**] 對話方塊隨即開啟。

6. 選取 [ **C/C++**  ] 節點。

7. 在 [**其他 Include 目錄**] 欄位中，指定 DirectX Include 資料夾的位置。 此資料夾的預設位置是%ProgramFiles%\Microsoft DirectX SDK （*version*） \Include。

8. 按兩下 [**連結器**] 節點，將它展開。

9. 在 [**其他程式庫目錄**] 欄位中，指定 DirectX 程式庫資料夾的位置。 此資料夾的預設位置是%ProgramFiles%\Microsoft DirectX SDK （*version*） \Lib\x86。

10. 選取 [**輸入**] 節點。

11. 在 [**其他**相依性] 欄位中`d3d9.lib` ， `d3dx9.lib`新增和檔案。

12. 在方案總管中，將名`D3DContent.def`為的新模組定義檔案（.def）新增至專案。

## <a name="creating-the-direct3d9-content"></a>建立 Direct3D9 內容
 若要獲得最佳效能，您的 Direct3D9 內容必須使用特定設定。 下列程式碼顯示如何建立具有最佳效能特性的 Direct3D9 介面。 如需詳細資訊，請參閱[Direct3D9 和 WPF 互通性的效能考慮](performance-considerations-for-direct3d9-and-wpf-interoperability.md)。

#### <a name="to-create-the-direct3d9-content"></a>建立 Direct3D9 內容

1. 使用方案總管，將三C++個類別新增至名為的專案，如下所示。

     `CRenderer`（使用虛擬的析構函式）

     `CRendererManager`

     `CTriangleRenderer`

2. 在程式碼編輯器中開啟轉譯器 .h，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. 在程式碼編輯器中開啟轉譯程式 .cpp，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. 在程式碼編輯器中開啟 RendererManager，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. 在程式碼編輯器中開啟 RendererManager，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. 在程式碼編輯器中開啟 TriangleRenderer，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. 在程式碼編輯器中開啟 TriangleRenderer，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. 在程式碼編輯器中開啟 stdafx.h，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. 在程式碼編輯器中開啟 dllmain .cpp，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. 在程式碼編輯器中開啟 D3DContent。

11. 使用下列程式碼取代自動產生的程式碼。

    ```cpp
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. 建置專案。

## <a name="next-steps"></a>後續步驟

- 將 Direct3D9 內容裝載于 WPF 應用程式中。 如需詳細資訊，請參閱[逐步解說：在 WPF](walkthrough-hosting-direct3d9-content-in-wpf.md)中裝載 Direct3D9 內容。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 和 WPF 互通性的效能考量](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [逐步解說：在 WPF 中裝載 Direct3D9 內容](walkthrough-hosting-direct3d9-content-in-wpf.md)
