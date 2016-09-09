## IOS block

> Block经常用到也非常实用，下面是他的定义与使用。

### 定义

* .h文件


		typedefvoid (^CompletionBlock)(UIImage *image);
    -(void)takeScreenshot:(CompletionBlock)block;


* .M文件

		- (void)takeScreenshot:(CompletionBlock)block
		{
    		dispatch_queue_t queue = dispatch_queue_create("screenshot", 0);
    		dispatch_async(queue, ^(void) {

        	UIGraphicsBeginImageContextWithOptions(self.frame.size, NO, 0.0);
        	[self.layerrenderInContext:UIGraphicsGetCurrentContext()];

        	UIImage *screenshot = UIGraphicsGetImageFromCurrentImageContext();
        	UIGraphicsEndImageContext();

        	dispatch_async(dispatch_get_main_queue(), ^{
            block(screenshot);
        	});
        	dispatch_release(queue);
    		});
		}

* 引用文件

		[self takeScreenshot:^(UIImage *image) {
        //do something...
    	}];
