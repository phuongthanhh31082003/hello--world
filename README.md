# hello--world
// Bạn có thể thay đổi các biến toàn cục tại đây:
var  bán kính  =  240 ;  // bán kính lớn bao nhiêu
var  autoRotate  =  true ;  // tự động xoay hay không
var  xoaySpeed  =  - 60 ;  // đơn vị: giây / 360 độ
var  imgWidth  =  120 ;  // chiều rộng của hình ảnh (đơn vị: px)
var  imgHeight  =  170 ;  // chiều cao của hình ảnh (đơn vị: px)

// Liên kết của nhạc nền - đặt 'null' nếu bạn không muốn phát nhạc nền
var  bgMusicURL  =  'https://api.soundcloud.com/tracks/143041228/stream?client_id=587aa2d384f7333a886010d5f52f302a' ;
var  bgMusicControls  =  true ;  // Hiển thị điều khiển nhạc giao diện người dùng



// ===================== bắt đầu =======================
// hoạt ảnh bắt đầu sau 1000 mili giây
setTimeout ( init ,  1000 ) ;

var  odrag  =  tài liệu . getElementById ( 'vùng chứa kéo' ) ;
var  ospin  =  tài liệu . getElementById ( 'spin-container' ) ;
var  aImg  =  ospin . getElementsByTagName ( 'img' ) ;
var  aVid  =  ospin . getElementsByTagName ( 'video' ) ;
var  aEle  =  [ ... aImg , ... aVid ] ;  // kết hợp 2 mảng

// Kích thước của hình ảnh
ospin . phong cách . width  =  imgWidth  +  "px" ;
ospin . phong cách . chiều cao  =  imgHeight  +  "px" ;

// Kích thước của mặt đất - phụ thuộc vào bán kính
var  ground  =  tài liệu . getElementById ( 'mặt đất' ) ;
mặt đất . phong cách . chiều rộng  =  bán kính  *  3  +  "px" ;
mặt đất . phong cách . chiều cao  =  bán kính  *  3  +  "px" ;

function  init ( delayTime )  {
  for  ( var  i  =  0 ;  i  <  aEle . length ;  i ++ )  {
    aEle [ i ] . phong cách . biến đổi  =  "xoayY ("  +  ( i  *  ( 360  /  aEle . length ) )  +  "deg) translateZ ("  +  radius  +  "px)" ;
    aEle [ i ] . phong cách . chuyển đổi  =  "biến đổi 1s" ;
    aEle [ i ] . phong cách . chuyển  tiếpDelay =  delayTime  ||  ( aEle . length  -  i )  /  4  +  "s" ;
  }
}

function  applyTranform ( obj )  {
  // Giới hạn góc máy ảnh (từ 0 đến 180)
  nếu ( tY  >  180 )  tY  =  180 ;
  nếu ( tY  <  0 )  tY  =  0 ;

  // Áp dụng góc
  phản đối . phong cách . biến đổi  =  "xoayX ("  +  ( - tY )  +  "deg) xoayY ("  +  ( tX )  +  "deg)" ;
}

function  playSpin ( có )  {
  ospin . phong cách . animationPlayState  =  ( có ? 'running' : 'tạm dừng' ) ;
}

var  SX ,  sY ,  nX ,  NY ,  desX  =  0 ,
    desY  =  0 ,
    tX  =  0 ,
    tY  =  10 ;

// tự động quay
if  ( autoRotate )  {
  var  animationName  =  ( xoaySpeed  >  0 ? 'spin' : 'spinRevert' ) ;
  ospin . phong cách . animation  =  ` $ { animationName }  $ { Toán học . abs ( xoaySpeed ) } s tuyến tính vô hạn` ;
}

// thêm nhạc nền
nếu  ( bgMusicURL )  {
  tài liệu . getElementById ( 'music-container' ) . innerHTML  + =  `
<audio src = " $ { bgMusicURL } " $ { bgMusicControls ? 'control' : '' } vòng lặp tự động phát>    
<p> Nếu bạn đang đọc nội dung này, đó là do trình duyệt của bạn không hỗ trợ phần tử âm thanh. </p>
</audio>
` ;
}

// thiết lập sự kiện
tài liệu . onpointerdown  =  function  ( e )  {
  clearInterval ( bộ đếm thời gian odrag . ) ;
  e  =  e  ||  cửa sổ . sự kiện ;
  var  sX  =  e . clientX ,
      sY  =  e . khách hàngY ;

  cái này . onpointermove  =  function  ( e )  {
    e  =  e  ||  cửa sổ . sự kiện ;
    var  nX  =  e . clientX ,
        nY  =  e . khách hàngY ;
    desX  =  nX  -  sX ;
    DESY  =  NY  -  sY ;
    tX  + =  desX  *  0,1 ;
    tY  + =  desY  *  0,1 ;
    applyTranform ( odrag ) ;
    sX  =  nX ;
    sY  =  nY ;
  } ;

  cái này . onpointerup  =  function  ( e )  {
    odrag . timer  =  setInterval ( function  ( )  {
      desX  * =  0,95 ;
      desY  * =  0,95 ;
      tX  + =  desX  *  0,1 ;
      tY  + =  desY  *  0,1 ;
      applyTranform ( odrag ) ;
      playSpin ( sai ) ;
      if  ( Math . abs ( desX )  <  0.5  &&  Math . abs ( desY )  <  0.5 )  {
        clearInterval ( bộ đếm thời gian odrag . ) ;
        playSpin ( true ) ;
      }
    } ,  17 ) ;
    cái này . onpointermove  =  cái này . onpointerup  =  null ;
  } ;

  trả về  sai ;
} ;

tài liệu . onmousewheel  =  function ( e )  {
  e  =  e  ||  cửa sổ . sự kiện ;
  var  d  =  e . wheelDelta  /  20  ||  - e . chi tiết ;
  bán kính  + =  d ;
  init ( 1 ) ;
} ;



















var  canvas  =  document . getElementById ( "canvas" ) ;

vải bạt . chiều rộng  =  cửa sổ . chiều rộng bên trong ;
vải bạt . chiều cao  =  cửa sổ . chiều cao bên trong ;

// Khởi tạo ngữ cảnh GL
var  gl  =  canvas . getContext ( 'webgl' ) ;
if ( ! gl ) {
  bàn điều khiển . error ( "Không thể khởi tạo WebGL." ) ;
}

//Thời gian
 thời gian  var =  0,0 ;

// ************** Nguồn Shader **************

var  vertexSource  =  `
thuộc tính vec2 vị trí;
void main () {
	gl_Position = vec4 (vị trí, 0.0, 1.0);
}
` ;

var  fragmentSource  =  '
Phao highp chính xác;
chiều rộng phao đồng nhất;
chiều cao phao đồng nhất;
độ phân giải vec2 = vec2 (chiều rộng, chiều cao);
thời gian trôi đồng nhất;
#define POINT_COUNT 8
vec2 điểm [POINT_COUNT];
const float speed = -0,5;
const float len ​​= 0,25;
cường độ phao = 1,3;
bán kính phao = 0,008;
//https://www.shadertoy.com/view/MlKcDD
// Khoảng cách đã ký đến một bezier bậc hai
float sdBezier (vec2 pos, vec2 A, vec2 B, vec2 C) {    
	vec2 a = B - A;
	vec2 b = A - 2.0 * B + C;
	vec2 c = a * 2.0;
	vec2 d = A - pos;
	float kk = 1.0 / dot (b, b);
	float kx = kk * dot (a, b);
	float ky = kk * (2.0 * dot (a, a) + dot (d, b)) / 3.0;
	float kz = kk * dot (d, a);      
	float res = 0.0;
	float p = ky - kx * kx;
	float p3 = p * p * p;
	float q = kx * (2.0 * kx * kx - 3.0 * ky) + kz;
	float h = q * q + 4.0 * p3;
	nếu (h> = 0.0) { 
		h = sqrt (h);
		vec2 x = (vec2 (h, -h) - q) / 2.0;
		vec2 uv = sign (x) * pow (abs (x), vec2 (1.0 / 3.0));
		float t = uv.x + uv.y - kx;
		t = kẹp (t, 0,0, 1,0);
		// 1 gốc
		vec2 qos = d + (c + b * t) * t;
		res = chiều dài (qos);
	}khác{
		float z = sqrt (-p);
		float v = acos (q / (p * z * 2.0)) / 3.0;
		float m = cos (v);
		float n = sin (v) * 1.732050808;
		vec3 t = vec3 (m + m, -n - m, n - m) * z - kx;
		t = kẹp (t, 0,0, 1,0);
		// 3 gốc
		vec2 qos = d + (c + b * tx) * tx;
		float dis = dot (qos, qos);
        
		res = dis;
		qos = d + (c + b * ty) * ty;
		dis = dấu chấm (qos, qos);
		res = min (res, dis);
		
		qos = d + (c + b * tz) * tz;
		dis = dấu chấm (qos, qos);
		res = min (res, dis);
		res = sqrt (res);
	}
    
	trả lại res;
}
//http://mathworld.wolfram.com/HeartCurve.html
vec2 getHeartPosition (float t) {
	return vec2 (16.0 * sin (t) * sin (t) * sin (t),
							- (13.0 * cos (t) - 5.0 * cos (2.0 * t)
							- 2.0 * cos (3.0 * t) - cos (4.0 * t)));
}
//https://www.shadertoy.com/view/3s3GDn
float getGlow (float dist, float radius, float boost) {
	trả về pow (bán kính / dist, cường độ);
}
float getSegment (float t, vec2 pos, float offset, float scale) {
	for (int i = 0; i <POINT_COUNT; i ++) {
		points [i] = getHeartPosition (offset + float (i) * len + fract (speed * t) * 6.28);
	}
    
	vec2 c = (điểm [0] + điểm [1]) / 2,0;
	vec2 c_prev;
	float dist = 10000.0;
    
	for (int i = 0; i <POINT_COUNT-1; i ++) {
		//https://tinyurl.com/y2htbwkm
		c_prev = c;
		c = (điểm [i] + điểm [i + 1]) / 2,0;
		dist = min (dist, sdBezier (pos, scale * c_prev, scale * points [i], scale * c));
	}
	trả về tối đa (0.0, dist);
}
void main () {
	vec2 uv = gl_FragCoord.xy / Resolution.xy;
	float widthHeightRatio = Resolution.x / Resolution.y;
	vec2 center = vec2 (0,5, 0,5);
	vec2 pos = center - uv;
	pos.y / = widthHeightRatio;
	// Di chuyển lên trên đến giữa trái tim
	pos.y + = 0,02;
	quy mô float = 0,000015 * chiều cao;
	
	float t = thời gian;
    
	// Nhận phân đoạn đầu tiên
  float dist = getSegment (t, pos, 0.0, scale);
  float glow = getGlow (dist, bán kính, cường độ);
  
  vec3 col = vec3 (0.0);
	// Lõi trắng
  col + = 10.0 * vec3 (Smoothstep (0,003, 0,001, dist));
  // Ánh sáng hồng
  col + = glow * vec3 (1.0,0.05.0.3);
  
  // Nhận phân đoạn thứ hai
  dist = getSegment (t, pos, 3,4, scale);
  glow = getGlow (dist, bán kính, cường độ);
  
  // Lõi trắng
  col + = 10.0 * vec3 (Smoothstep (0,003, 0,001, dist));
  // Ánh sáng xanh lam
  col + = glow * vec3 (0,1,0.4,1.0);
        
	//Chỉnh sửa ánh sáng
	col = 1,0 - exp (-col);
	// Gamma
	col = pow (col, vec3 (0,4545));
	// Xuất ra màn hình
 	gl_FragColor = vec4 (col, 1.0);
}
` ;

//************** Các chức năng tiện ích **************

cửa sổ . addEventListener ( 'thay đổi kích thước' ,  onWindowResize ,  false ) ;

function  onWindowResize ( ) {
  vải bạt . chiều rộng   =  cửa sổ . chiều rộng bên trong ;
  vải bạt . chiều cao  =  cửa sổ . chiều cao bên trong ;
	gl . khung nhìn ( 0 ,  0 ,  canvas . width ,  canvas . height ) ;
  gl . Uniform1f ( widthHandle ,  window . innerWidth ) ;
  gl . Uniform1f ( heightHandle ,  window . innerHeight ) ;
}


// Biên dịch shader và kết hợp với mã nguồn
function  compileShader ( shaderSource ,  shaderType ) {
  var  shader  =  gl . createShader ( shaderType ) ;
  gl . shaderSource ( đổ bóng ,  shaderSource ) ;
  gl . compileShader (trình đổ bóng ) ;
  if ( ! gl . getShaderParameter ( shader ,  gl . COMPILE_STATUS ) ) {
  	ném  "Biên dịch Shader không thành công với:"  +  gl . getShaderInfoLog ( đổ bóng ) ;
  }
  trả lại  shader ;
}

// Từ https://codepen.io/jlfwong/pen/GqmroZ
// Tiện ích phàn nàn lớn tiếng nếu chúng tôi không tìm thấy thuộc tính / đồng phục
function  getAttribLocation ( chương trình ,  tên )  {
  var  thuộc  tínhLocation =  gl . getAttribLocation ( chương trình ,  tên ) ;
  if  ( thuộc  tínhLocation ===  - 1 )  {
  	ném  'Không thể tìm thấy thuộc tính'  +  tên  +  '.' ;
  }
  trả về  thuộc tínhLocation ;
}

function  getUniformLocation ( chương trình ,  tên )  {
  var  thuộc  tínhLocation =  gl . getUniformLocation ( chương trình ,  tên ) ;
  if  ( thuộc  tínhLocation ===  - 1 )  {
  	ném  'Không thể tìm thấy đồng phục'  +  tên  +  '.' ;
  }
  trả về  thuộc tínhLocation ;
}

// ************** Tạo bóng đổ **************

// Tạo bóng đổ đỉnh và phân mảnh
var  vertexShader  =  compileShader ( vertexSource ,  gl . vERTEX_SHADER ) ;
var  fragmentShader  =  compileShader ( fragmentSource ,  gl . FRAGMENT_SHADER ) ;

// Tạo chương trình đổ bóng
 chương trình  var =  gl . createProgram ( ) ;
gl . AttachShader ( chương trình ,  vertexShader ) ;
gl . mountShader ( chương trình ,  phân mảnh ) ;
gl . linkProgram ( chương trình ) ;

gl . useProgram ( chương trình ) ;

// Thiết lập hình chữ nhật bao phủ toàn bộ canvas 
var  vertexData  =  new  Float32Array ( [
  - 1.0 ,   1.0 ,  	// trên cùng bên trái
  - 1.0 ,  - 1.0 ,  	// dưới cùng bên trái
   1.0 ,   1.0 ,  	// trên cùng bên phải
   1.0 ,  - 1.0 ,  	// dưới cùng bên phải
] ) ;

// Tạo bộ đệm đỉnh
var  vertexDataBuffer  =  gl . createBuffer ( ) ;
gl . bindBuffer ( gl . ARRAY_BUFFER ,  vertexDataBuffer ) ;
gl . bufferData ( gl . ARRAY_BUFFER ,  vertexData ,  gl . STATIC_DRAW ) ;

// Bố trí dữ liệu của chúng ta trong bộ đệm đỉnh
var  positionHandle  =  getAttribLocation ( chương trình ,  'vị trí' ) ;

gl . enableVertexAttribArray ( positionHandle ) ;
gl . vertexAttribPointer ( positionHandle ,
  2 ,  				// vị trí là vec2 (2 giá trị cho mỗi thành phần)
  gl . FLOAT ,  // mỗi thành phần là một float
  false ,  		// không chuẩn hóa các giá trị
  2  *  4 ,  		// hai thành phần float 4 byte cho mỗi đỉnh (float 32 bit là 4 byte)
  0  				// có bao nhiêu byte bên trong bộ đệm để bắt đầu từ
  ) ;

// Đặt tay cầm thống nhất
var  timeHandle  =  getUniformLocation ( chương trình ,  'thời gian' ) ;
var  widthHandle  =  getUniformLocation ( chương trình ,  'width' ) ;
var  heightHandle  =  getUniformLocation ( chương trình ,  'chiều cao' ) ;

gl . Uniform1f ( widthHandle ,  window . innerWidth ) ;
gl . Uniform1f ( heightHandle ,  window . innerHeight ) ;

var  lastFrame  =  Ngày . ngay ( ) ;
var  thisFrame ;

hàm  draw ( ) {
	
  //Cập nhật thời gian
	thisFrame  =  Ngày . ngay ( ) ;
  time  + =  ( thisFrame  -  lastFrame ) / 1000 ;	
	lastFrame  =  thisFrame ;

	// Gửi đồng phục đến chương trình
  gl . Uniform1f ( timeHandle ,  time ) ;
  // Vẽ một dải tam giác nối các đỉnh 0-4
  gl . drawArrays ( gl . TRIANGLE_STRIP ,  0 ,  4 ) ;

  requestAnimationFrame ( vẽ ) ;
}

draw ( ) ;
© 2021 GitHub, Inc.
Điều kiện
Sự riêng

