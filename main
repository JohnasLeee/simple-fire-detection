import cv2
import numpy as np

cap = cv2.VideoCapture(0)

while True:
    _, frame = cap.read()
    hsv_frame = cv2.cvtColor(frame, cv2.COLOR_BGR2HSV)

    #red
    low_red = np.array([14, 180, 150])
    high_red = np.array([35, 255, 255])
    #orange
    low_org = np.array([35, 100, 40])
    high_org = np.array([57, 255, 255])
    #mask
    red_mask = cv2.inRange(hsv_frame, low_red, high_red)
    org_mask = cv2.inRange(hsv_frame, low_org, high_org)

    mask_red = cv2.inRange(hsv_frame, low_red, high_red)
    mask_org = cv2.inRange(hsv_frame, low_org, high_org)
    red = cv2.bitwise_and(frame, frame, mask=red_mask)
    org = cv2.bitwise_and(frame, frame, mask=org_mask)

    fire_pixels_red = cv2.countNonZero(mask_red)
    fire_pixels_org = cv2.countNonZero(mask_org)

    print(fire_pixels_red, " ", fire_pixels_org)

    cv2.imshow("Frame", frame)
    cv2.imshow("Red", red)


    key = cv2.waitKey(1)

    if key == 27:
        break

    if int(fire_pixels_red + fire_pixels_org) > 2000:
        print("True")

    else:
        pass
