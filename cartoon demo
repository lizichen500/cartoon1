#include <opencv2/opencv.hpp>
#include <iostream>


using namespace std;
using namespace cv;


int main() {
	Mat src;
	namedWindow("原图像", WINDOW_NORMAL);
	namedWindow("cartoon", WINDOW_NORMAL);
	namedWindow("cartoon_image",WINDOW_NORMAL);

	//src = imread("C:\\Users\\Lenovo\\Desktop\\cartoon\\柳萌2.jpg");
	src = imread("F:\\yuhsi.jpg");
	if (!src.data)
	{
		printf("can't load the picture\n");
		return -1;
	}
	
	imshow("原图像", src);
	Mat gray, gaussian, edgeImage, edgePreservingImage,cartoon_image;
	Mat output = Mat::zeros(src.size(), src.type());
	imshow("123", output);
	cvtColor(src, gray, COLOR_BGR2GRAY);

	GaussianBlur(gray, gray, Size(5, 5), 0);

	Laplacian(gray, edgeImage, -1, 5);
	edgeImage = 255 - edgeImage;
	threshold(edgeImage, edgeImage, 150, 255, THRESH_BINARY);

	edgePreservingFilter(src, edgePreservingImage, 2, 50, 0.4);

	

	bitwise_and(edgePreservingImage, edgePreservingImage, output, edgeImage);
	imshow("cartoon",output);
    stylization(src,cartoon_image,150,0.25);
	namedWindow("1234", WINDOW_NORMAL);

	imshow("1234",cartoon_image);
	Mat frame1, frame2;

	pencilSketch(src,frame1,frame2,65,0.5,0.02);
	namedWindow("pencil1",WINDOW_NORMAL);
	namedWindow("pencil2",WINDOW_NORMAL);


	imshow("pencil1",frame1);
	imshow("pencil2",frame2);

	imwrite("11111.jpg",cartoon_image);
	imwrite("2222.jpg", frame1);
	imwrite("3333.jpg", frame2);

	printf("12345678");
	waitKey(0);
	return 0;
}
