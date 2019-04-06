---
title: Linux 사용자 계정 및 사용 권한
description: Linux 용 Windows 하위 시스템을 사용 하 여 사용자 계정 및 사용 권한 관리에 대 한 참조입니다.
keywords: BashOnWindows, bash, wsl, windows, linux, windowssubsystem, ubuntu, 사용자 계정에 대 한 windows 하위 시스템
author: scooley
ms.author: scooley
ms.date: 09/11/2017
ms.topic: article
ms.assetid: f70e685f-24c6-4908-9546-bf4f0291d8fd
ms.custom: seodec18
ms.openlocfilehash: 5820d701d5c0e22f14bf76e3dc6fe70bacb5213a
ms.sourcegitcommit: ca08a78925880ed3eccf88edb30def16c83f2543
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/04/2019
ms.locfileid: "59063601"
---
# <a name="user-accounts-and-permissions-for-windows-subsystem-for-linux"></a><span data-ttu-id="ae9ae-104">사용자 계정 및 Linux 용 Windows 하위 시스템에 대 한 권한</span><span class="sxs-lookup"><span data-stu-id="ae9ae-104">User Accounts and Permissions for Windows Subsystem for Linux</span></span>

<span data-ttu-id="ae9ae-105">WSL에서 새 Linux 배포를 설정 하는 첫 번째 단계는 Linux 사용자를 만들기.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-105">Creating your Linux user is the first step in setting up a new Linux distribution on WSL.</span></span>  <span data-ttu-id="ae9ae-106">사용자가 만든 첫 번째 사용자 계정에 몇 가지 특수 한 특성을 사용 하 여 자동으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-106">The first user account you create is automatically configured with a few special attributes:</span></span>

1. <span data-ttu-id="ae9ae-107">기본 사용자 것-해당 로그인 자동으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-107">It is your default user -- it signs-in automatically on launch.</span></span>
1. <span data-ttu-id="ae9ae-108">기본적으로 Linux 관리자 (sudo 그룹의 구성원)는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-108">It is Linux administrator (a member of the sudo group) by default.</span></span>

<span data-ttu-id="ae9ae-109">Linux 용 Windows 하위 시스템에서 실행 중인 각 Linux 배포에는 자체 Linux 사용자 계정 및 암호.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-109">Each Linux distribution running on the Windows Subsystem for Linux has its own Linux user accounts and passwords.</span></span>  <span data-ttu-id="ae9ae-110">언제 든 지 추가 배포를 다시 설치 또는 다시 설정 Linux 사용자 계정을 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-110">You will have to configure a Linux user account any time you add a distribution, reinstall, or reset.</span></span>  <span data-ttu-id="ae9ae-111">와 별개의 Windows 사용자 계정에도, Linux 사용자 계정 에서만 배포당 독립 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-111">Linux user accounts are not only independent per distribution, they are also independent from your Windows user account.</span></span>

## <a name="resetting-your-linux-password"></a><span data-ttu-id="ae9ae-112">Linux 암호를 다시 설정</span><span class="sxs-lookup"><span data-stu-id="ae9ae-112">Resetting your Linux password</span></span>

<span data-ttu-id="ae9ae-113">변경할 현재 암호를 알고 있고 Linux 사용자 계정에 액세스할 경우 Linux를 사용 하 여 암호 재설정 해당 배포-가장 가능성이 높은 도구 `passwd`합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-113">If you have access to your Linux user account and know your current password, change it using Linux password reset tools of that distribution -- most likely `passwd`.</span></span>

<span data-ttu-id="ae9ae-114">배포에 따라 옵션 하지 않은 경우에 기본 사용자를 다시 설정 하 여 암호를 재설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-114">If that's not an option, depending on the distribution, you may be able to reset your password by resetting the default user.</span></span>

<span data-ttu-id="ae9ae-115">WSL은 사용자 계정을 자동으로 식별 하는 기본 사용자 태그는 WSL 시작할 때 로그인을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-115">WSL offers a default user tag to identify which user account automatically logs in when you start a WSL.</span></span>  <span data-ttu-id="ae9ae-116">대부분의 배포 루트 및 루트 사용자로 설정 된 암호가 없거나를 사용 하 여 기본 사용자를 설정 하는 명령을 포함 하므로 기본 사용자 루트 변경은 등 암호 재설정에 대 한 유용한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-116">Since many distributions include commands to set the default user to root and also a root user with no password set, changing the default user to root is a handy tool for things like password reset.</span></span>

### <a name="for-creators-update-and-earlier"></a><span data-ttu-id="ae9ae-117">크리에이터 스 업데이트 이상</span><span class="sxs-lookup"><span data-stu-id="ae9ae-117">For Creators Update and earlier</span></span>
<span data-ttu-id="ae9ae-118">실행 중인 경우 Windows 10 크리에이터 스 업데이트 하거나 이전에 다음 명령을 실행 하 여 기본 Bash 사용자를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-118">If you're running Windows 10 Creators update or earlier, you can change the default Bash user by running the following commands:</span></span>

1. <span data-ttu-id="ae9ae-119">기본 사용자 변경 `root`:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-119">Change the default user to `root`:</span></span>

    ```console
    C:\> lxrun /setdefaultuser root
    ```

1. <span data-ttu-id="ae9ae-120">실행할 `bash.exe` 지금 로그인으로 `root`:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-120">Run `bash.exe` to now login as `root`:</span></span>

    ```console
    C:\> bash.exe
    ```

1. <span data-ttu-id="ae9ae-121">분포의 암호 명령을 사용 하 여 암호를 재설정 하 고 Linux 콘솔을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-121">Reset your password using the distribution's password command, and close the Linux Console:</span></span>

    ```BASH
    $ passwd username
    $ exit
    ```

1. <span data-ttu-id="ae9ae-122">Windows CMD에서 일반적인 Linux 사용자 계정으로 다시 기본 사용자를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-122">From Windows CMD, reset your default user back to your normal Linux user account:</span></span>

    ```console
    C:\> lxrun.exe /setdefaultuser username
    ```

### <a name="for-fall-creators-update-and-later"></a><span data-ttu-id="ae9ae-123">Fall Creators Update에 대 한 이상</span><span class="sxs-lookup"><span data-stu-id="ae9ae-123">For Fall Creators Update and later</span></span>
<span data-ttu-id="ae9ae-124">특정 배포에 사용할 수 있는 명령을 확인 하려면 `[distro.exe] /?`합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-124">To see what commands are available for a particular distribution, run `[distro.exe] /?`.</span></span>
    
<span data-ttu-id="ae9ae-125">예를 들어, Ubuntu를 사용 하 여 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-125">For example, with Ubuntu installed:</span></span>

```console
C:\> ubuntu.exe /?

Launches or configures a linux distribution.

Usage:
    <no args>
      - Launches the distro's default behavior. By default, this launches your default shell.

    run <command line>
      - Run the given command line in that distro, using the default configuration.
      - Everything after `run ` is passed to the linux LaunchProcess cal

    config [setting [value]]
      - Configure certain settings for this distro.
      - Settings are any of the following (by default)
        - `--default-user <username>`: Set the default user for this distro to <username>

    clean
      - Uninstalls the distro. The appx remains on your machine. This can be
        useful for "factory resetting" your instance. This removes the linux
        filesystem from the disk, but not the app from your PC, so you don't
        need to redownload the entire tar.gz again.

    help
      - Print this usage message.
```

<span data-ttu-id="ae9ae-126">Ubuntu를 사용 하는 단계별 지침 단계:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-126">Step by step instructions using Ubuntu:</span></span>

1. <span data-ttu-id="ae9ae-127">열기 CMD</span><span class="sxs-lookup"><span data-stu-id="ae9ae-127">Open CMD</span></span>
1. <span data-ttu-id="ae9ae-128">기본 Linux 사용자로 `root`:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-128">Set the default Linux user to `root`:</span></span>

    ```console
    C:\> ubuntu config --default-user root
    ```    

1. <span data-ttu-id="ae9ae-129">Linux 배포를 시작 (`ubuntu`).</span><span class="sxs-lookup"><span data-stu-id="ae9ae-129">Launch your Linux distribution (`ubuntu`).</span></span>  <span data-ttu-id="ae9ae-130">자동으로로 로그인 `root`:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-130">You will automatically login as `root`:</span></span>

1. <span data-ttu-id="ae9ae-131">사용 하 여 암호 재설정을 `passwd` 명령:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-131">Reset your password using the `passwd` command:</span></span>

    ```BASH
    $ passwd username
    ```

1. <span data-ttu-id="ae9ae-132">Windows CMD에서 일반적인 Linux 사용자 계정으로 다시 기본 사용자를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-132">From Windows CMD, reset your default user back to your normal Linux user account.</span></span>

    ```console
    C:\> ubuntu config --default-user username
    ```

## <a name="permissions"></a><span data-ttu-id="ae9ae-133">사용 권한</span><span class="sxs-lookup"><span data-stu-id="ae9ae-133">Permissions</span></span>

<span data-ttu-id="ae9ae-134">WSL에서 사용 권한을 제공 하는 경우 염두에 두 가지 중요 한 개념이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-134">There are two important concepts to keep in mind when it comes to permissions in WSL:</span></span>

1. <span data-ttu-id="ae9ae-135">Windows 권한 모델을 Windows 리소스에 대 한 프로세스의 권한을 제어합니다</span><span class="sxs-lookup"><span data-stu-id="ae9ae-135">The Windows permission model governs a process' rights to Windows resources</span></span>
2. <span data-ttu-id="ae9ae-136">Linux 권한 모델에는 Linux 리소스에 대 한 프로세스의 권한을 제어합니다</span><span class="sxs-lookup"><span data-stu-id="ae9ae-136">The Linux permission model controls a process' rights to Linux resources</span></span>

<span data-ttu-id="ae9ae-137">WSL에서 Linux를 실행 하는 경우 Linux는 프로세스와 동일한 Windows 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-137">When running Linux on WSL, Linux will have the same Windows permissions as the process that launches it.</span></span> <span data-ttu-id="ae9ae-138">두 사용 권한 수준 중 하나로 Linux는 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-138">Linux can be launched in one of two permission levels:</span></span>

* <span data-ttu-id="ae9ae-139">일반 (권한이 상승 되지 않은): Linux에서 로그인 한 사용자의 권한으로 실행</span><span class="sxs-lookup"><span data-stu-id="ae9ae-139">Normal (non-elevated): Linux runs with the permissions of the logged-in user</span></span>
* <span data-ttu-id="ae9ae-140">관리자 권한/관리자: 관리자 권한/관리자 Windows 권한으로 실행 되는 Linux</span><span class="sxs-lookup"><span data-stu-id="ae9ae-140">Elevated/admin: Linux runs with elevated/admin Windows permissions</span></span>

> <span data-ttu-id="ae9ae-141">상승 된 때문에 프로세스 수 변경/시스템 차원의 설정 및 데이터 손상과 보호 파일 및 폴더 액세스/수정 **하지 말고** Windows 있는지 여부에 반드시 필요한 경우가 아니면 관리자 권한 프로세스를 시작 하거나 Linux 응용 프로그램/도구/셸!</span><span class="sxs-lookup"><span data-stu-id="ae9ae-141">Because that elevated processes can change/damage system-wide settings and data, and can access/modify protected files and folders, **AVOID** launching elevated processes unless you absolutely have to - whether they're Windows or Linux applications/tools/shells!</span></span>

<span data-ttu-id="ae9ae-142">위의 Windows 권한은 Linux 인스턴스 내에서 사용 권한을 무관 다음과 같습니다. "루트 권한" Linux Linux 환경 및 파일 시스템 내에서 사용자의 권한에 영향을 줍니다. 영향을 미치지 않습니다 Windows 권한 부여에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-142">The above Windows permissions are independent of the permissions within a Linux instance: Linux "Root privileges" only impact the user’s rights within the Linux environment & filesystem; they have no impact on the Windows privileges granted.</span></span> <span data-ttu-id="ae9ae-143">따라서 루트로 Linux 프로세스를 실행 (예: 통해 `sudo`) Linux 환경 내에서 권한 관리를 처리 하는 유일한 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-143">Thus, running a Linux process as root (e.g. via `sudo`) only grants that process admin rights within the Linux environment.</span></span>

**<span data-ttu-id="ae9ae-144">예:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-144">Example:</span></span>**    
<span data-ttu-id="ae9ae-145">Windows 관리자 권한으로 Bash 세션에 액세스할 수 있습니다 `cd /mnt/c/Users/Administrator` 관리자 권한이 사용 권한 거부 "오류를 볼 수 없는 Bash 세션 동안.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-145">A Bash session with Windows admin privileges may access `cd /mnt/c/Users/Administrator` while a Bash session without admin privileges would see a "Permission Denied" error.</span></span>

<span data-ttu-id="ae9ae-146">Linux에서 입력 `sudo cd /mnt/c/Users/Administrator` Windows 내에서 사용 권한을 Windows에서 관리 되므로 관리자의 디렉터리에 대 한 액세스 권한을 부여 하지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-146">In Linux, typing `sudo cd /mnt/c/Users/Administrator` will not grant access to the Administrator’s directory since permissions within Windows are managed by Windows.</span></span>

<span data-ttu-id="ae9ae-147">Linux 권한 모델이 사용자에 게 현재 Linux 사용자를 기반으로 하는 권한이 있는 Linux 환경 내에 있을 때 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-147">The Linux permission model is important when inside the Linux environment where the user has permissions based on the current Linux user.</span></span>

**<span data-ttu-id="ae9ae-148">예:</span><span class="sxs-lookup"><span data-stu-id="ae9ae-148">Example:</span></span>**  
<span data-ttu-id="ae9ae-149">Sudo 그룹에 사용자가 실행할 수 있습니다 `sudo apt update`합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ae-149">A user in the sudo group may run `sudo apt update`.</span></span>