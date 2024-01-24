# PLT_LC
If you want to make a light cone figure...
or Galaxy distribution map
or Redshift survey plot
or you have x, y, z potion data of galaxy or whatever.

If you need English Explanation, ask me (mmingyeong@kasi.re.kr)
or use Google translate.

# Introduction

이 코드는 Horizon Run 4의 Light Cone Data를 plot하기 위한 코드입니다.\
Kim, Juhan, et al. "Horizon Run 4 simulation: Coupled evolution of galaxies and large-scale structures of the Universe." arXiv preprint arXiv:1508.05107 (2015).

위 시뮬레이션에서 제공하는 여러 형식의 데이터 중에서 All-sky past lightcone data (out to z=1.5)를 plot합니다.
LC data는 아래와 같은 정보들을 제공합니다.
* Galaxy ID (8 bytes)
* X/Y/Z position in real space [cMpc/h] (8 bytes per each)
* X/Y/Z peculiar velocity [km/s] (4 bytes per each)
* Mass proxy (similar to subhalo mass) [Msun/h] (4 bytes)

우리는 X/Y/Z position 데이터를 사용하여 2차원 평면에 Galaxy 분포를 plot할 것입니다.

## Plot Algorithm
1. x,y,z dataset 준비
2. x,y,z dataset distribution histogram 확인
3. r, phi, theta dataset # 직교 좌표 데이터를 구면 좌표 데이터로 변환.
4. r, phi, theta dataset distribution histogram 확인 # 구면 좌표계의 phi
5. RA, DEC 범위 설정 # 위 histogram을 참고하여
6. plot할 r, phi dataset 추출.
7. plot dataset으로 극좌표계에 plot # 이때 r=z, phi=RA에 상응. # 극 좌표계의 phi

### USER Giude
snapshot -> 원하는 snapshot를 put\
dec -> projection 원하는 Declination (deg) put\
theta_mark_min = theta_mark - 10 # declination 범위 조정\
theta_mark_max = theta_mark + 10 # declination 범위 조정\
위는 delclination 기준 +10, -10 deg 범위이다.