mkdir px4_ccoss_workshop
cd px4_ccoss_workshop
git clone https://github.com/TOTON95/CCOSS_2022.git
git clone https://github.com/PX4/PX4-Autopilot.git
cd PX4-Autopilot
git submodule update --recursive --init
cd ..

sudo docker run -it -rm \
  -v /tmp/.x-unix:/tmp.X-unix:ro \
  -v /dev/dri:/dev/dri \
  -e DISPLAY=:$DISPLAY \
  -v $(pwd):/home/user/workspace/src \
  -v $(pwd)/PX4-Autopilot:/home/user/workspace/PX4-Autopilot \
  -e LOCAL_USER_ID="$(id -u)" \
  toton95/ccoss_px4_ros:latest