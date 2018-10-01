# lapa play moview
# -*- coding: utf-8 -*-
"""
Created on Fri Aug 24 19:52:41 2018
Play recorded avi file using open-cv
@author: whshi
"""
import os
import numpy as np
import cv2

fn = 'P16.avi'

cap = cv2.VideoCapture(fn)

def rescale_frame(frame, percent=75):
    width = int(frame.shape[1] * percent/ 100)
    height = int(frame.shape[0] * percent/ 100)
    dim = (width, height)
    return cv2.resize(frame,dim,interpolation = cv2.INTER_AREA)


while(cap.isOpened()):
    rect, frame = cap.read()
    frame75 = rescale_frame(frame, percent=25)
    cv2.imshow('frame75', frame75)

    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

cap.release()
cv2.destroyAllWindows()
