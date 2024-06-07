# ROOT-Xiaomi-Redmi-Note-10-Pro
### Xiaomi Redmi Note 10 Pro ROOT 
### สมัครหรือล็อคอิน
account.xiaomi.com/pass/register
### M2101K6G~Redmi Note 10 Pro
![Screenshot from 2024-06-08 02-10-18](https://github.com/valenzaa/ROOT-Xiaomi-Redmi-Note-10-Pro/assets/144785020/2c84c7d5-0dff-4603-a962-6fc589701356)
ROM https://ultimateota.d.miui.com/V14.0.8.0.TKFMIXM/miui_SWEETGlobal_V14.0.8.0.TKFMIXM_3e19ed98ed_13.0.zip?t=1717787626&s=1aa499aa6d34ba87febb7f53ef32cde4
https://new.c.mi.com/global/miuidownload/detail/device/1900389
การสร้าง Custom Recovery เอง (เช่น TWRP) สำหรับ Redmi Note 10 Pro บน Ubuntu ต้องใช้เครื่องมือพัฒนาและซอร์สโค้ดของ TWRP ซึ่งกระบวนการนี้จะต้องการความรู้ทางเทคนิคขั้นสูงและเวลาในการทำงาน
ขั้นตอนการสร้าง Custom Recovery สำหรับ Redmi Note 10 Pro

    การติดตั้งเครื่องมือพัฒนา:
        ติดตั้งแพ็กเกจที่จำเป็น:

        sh

    sudo apt update
    sudo apt install git-core repo gnupg flex bison gperf build-essential \
    zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
    lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z1-dev ccache \
    libgl1-mesa-dev libxml2-utils xsltproc unzip

ตั้งค่า Repo:

    ดาวน์โหลดและตั้งค่า Repo:

    sh

    mkdir ~/bin
    PATH=~/bin:$PATH
    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
    chmod a+x ~/bin/repo

ดาวน์โหลดซอร์สโค้ดของ TWRP:

    สร้างไดเรกทอรีใหม่สำหรับการทำงานและเริ่มใช้ Repo:

    sh

    mkdir twrp
    cd twrp
    repo init -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
    repo sync

ตั้งค่าซอร์สโค้ดสำหรับอุปกรณ์:

    สร้างไดเรกทอรีสำหรับอุปกรณ์ของคุณ (Redmi Note 10 Pro ใช้รหัส sweet):

    sh

    mkdir -p device/xiaomi/sweet
    cd device/xiaomi/sweet

    คัดลอกไฟล์กำหนดค่าของอุปกรณ์ (Android.mk, BoardConfig.mk, recovery.fstab) จากแหล่งที่เชื่อถือได้ หรือจากโครงการ TWRP ของอุปกรณ์ใกล้เคียง แล้วปรับแต่งตามความเหมาะสม

กำหนดค่าการสร้าง:

    กลับไปยังไดเรกทอรีหลักของ TWRP:

    sh

cd ~/twrp

ตั้งค่า environment variables:

sh

    export ALLOW_MISSING_DEPENDENCIES=true
    . build/envsetup.sh
    lunch omni_sweet-eng

สร้าง Custom Recovery:

    รันคำสั่งในการสร้าง:

    sh

    mka recoveryimage

แฟลช Recovery:

    เมื่อสร้างเสร็จแล้ว ไฟล์ recovery.img จะอยู่ใน out/target/product/sweet/recovery.img
    ใช้คำสั่ง Fastboot เพื่อแฟลชไฟล์ recovery.img:

    sh

        fastboot flash recovery out/target/product/sweet/recovery.img

หมายเหตุ

    การสำรองข้อมูล: ควรสำรองข้อมูลทั้งหมดก่อนทำการแฟลชหรือแก้ไขระบบ
    ความระมัดระวัง: กระบวนการนี้ซับซ้อนและมีความเสี่ยง ควรศึกษาและทำความเข้าใจทุกขั้นตอนอย่างละเอียด

แหล่งข้อมูลเพิ่มเติม

    TWRP Documentation
    XDA Developers Forum


