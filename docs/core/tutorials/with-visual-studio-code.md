---
title: "C# 및 Visual Studio Code-C# 설명서 시작"
description: "Visual Studio Code를 사용하여 C#에서 첫 번째 .NET Core 응용 프로그램을 만들고 디버그하는 방법을 알아봅니다."
keywords: "C#, 시작, 취득, 설치, Visual Studio Code, 플랫폼 간"
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 76c23597-4cf9-467e-8a47-0c3703ce37e7
ms.openlocfilehash: 3a9de689946507e4b6d89f684461d65049b3375a
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2017
---
# <a name="get-started-with-c-and-visual-studio-code"></a>C# 및 Visual Studio Code 시작

.NET Core는 Windows, Linux 및 macOS에서 실행되는 응용 프로그램을 만들기 위한 빠른 모듈식 플랫폼을 제공합니다. C# 확장이 있는 Visual Studio Code를 사용하면 C# IntelliSense(스마트 코드 완성) 및 디버깅을 완벽하게 지원하는 강력한 편집 환경이 구현됩니다.

## <a name="prerequisites"></a>필수 구성 요소

1. [Visual Studio Code](https://code.visualstudio.com/)를 설치합니다.
2. [.NET Core SDK](https://www.microsoft.com/net/download/core)를 설치합니다.
3. Visual Studio Code Marketplace에서 [C# 확장](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)을 설치합니다.

## <a name="hello-world"></a>Hello World

.NET Core에서 간단한 "Hello World" 프로그램으로 시작해 보겠습니다.

1. 프로젝트 열기

    * Visual Studio Code를 엽니다.
    * 왼쪽 메뉴에 있는 탐색기 아이콘을 클릭한 다음 **폴더 열기**를 클릭합니다.
    * 선택 **파일** > **폴더 열기** 하에 클릭 하 고 C# 프로젝트 폴더를 열어 주 메뉴에서 원하는 **폴더 선택**합니다. 이 예에서는 라는 프로젝트 진행에 대 한 폴더를 만드는 중입니다 *HelloWorld*합니다.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. C# 프로젝트 초기화
    * 선택 하 여 Visual Studio Code에서 통합 터미널 엽니다 **보기** > **통합 터미널** 주 메뉴에서 합니다.
    * 터미널 창에서 `dotnet new console`을 입력합니다.
    * 이 명령은 만듭니다는 `Program.cs` 라는 C# 프로젝트 파일과 함께 이미 작성 하는 간단한 "Hello World" 프로그램 폴더에 파일 `HelloWorld.csproj`합니다.

      ![dotnet new 명령](media/with-visual-studio-code/dotnetnew.png)

3. 빌드 자산 확인

    * 에 대 한 **.NET Core 1.x**, 형식 `dotnet restore`합니다. `dotnet restore`를 실행하면 프로젝트를 빌드하는 데 필요한 필수 .NET Core 패키지에 액세스할 수 있습니다.

      ![dotnet restore 명령](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. "Hello World" 프로그램 실행

    * `dotnet run`를 입력합니다. 

      ![dotnet run 명령](media/with-visual-studio-code/dotnetrun.png)

[Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS) 또는 [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)에 대한 추가 설치 도움말이 제공되는 짧은 비디오 자습서를 볼 수도 있습니다.

## <a name="debug"></a>디버그

1. *Program.cs*를 클릭하여 엽니다. 처음으로 Visual Studio 코드에서 C# 파일을 열면 [OmniSharp](http://www.omnisharp.net/) 편집기에 로드 합니다.

    ![Program.cs 파일 열기](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code을 빌드하고 앱을 디버그 하려면 누락 된 자산을 추가할 수 있습니다 메시지를 표시 해야 합니다. **예**를 선택합니다. 

    ![누락된 자산에 대한 프롬프트](media/with-visual-studio-code/missing-assets.png)

3. 디버그 보기를 열려면 왼쪽 메뉴에서 디버깅 아이콘을 클릭합니다.

    ![디버그 탭 열기](media/with-visual-studio-code/opendebug.png)

4. 창 위쪽에서 녹색 화살표를 찾습니다. 옆에 있는 드롭다운 목록에서 `.NET Core Launch (console)`가 선택되어 있는지 확인합니다.

    ![.NET Core 선택](media/with-visual-studio-code/selectcore.png)

5. 클릭 하 여 중단점을 프로젝트에 추가 **편집기 여백**, 공간인 9 줄 옆에 있는 편집기에서 줄 번호의 왼쪽에 있습니다.

    ![중단점 설정](media/with-visual-studio-code/setbreakpoint.png)

6. 디버깅을 시작 하려면 선택 <kbd>F5</kbd> 또는 녹색 화살표입니다. 이전 단계에서 설정한 중단점에 도달하면 디버거에서 프로그램 실행을 중지합니다.
    * 디버깅 하는 동안 로컬 변수 왼쪽된 상단 창에서 보거나 디버그 콘솔을 사용할 수 있습니다.

    ![실행 및 디버그](media/with-visual-studio-code/rundebug.png)

7. 디버깅을 계속하려면 위쪽에 있는 녹색 화살표를 선택하고, 중지하려면 위쪽의 빨간색 사각형을 선택합니다.

> [!TIP] 
> Visual Studio Code에서 OmniSharp를 사용한 .NET Core 디버깅에 대한 자세한 내용 및 문제 해결 정보는 [Instructions for setting up the .NET Core debugger](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)(.NET Core 디버거 설정 지침)를 참조하세요.

## <a name="see-also"></a>참고 항목
[Visual Studio Code 설정](https://code.visualstudio.com/docs/setup/setup-overview)   
[Visual Studio Code의 디버깅](https://code.visualstudio.com/Docs/editor/debugging)
