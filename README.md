# geo-fence
Ever wonder how **YikYak** figures out how to do geo-fencing. Below is the script for an API that's ready for your app. Go to [SaturnAPI.com](https://saturnapi.com) and learn more about other APIs and or make a request.

```
%%%%%%%%%%%%%%%%%%%%%%%%%% GEO-FENCING %%%%%%%%%%%%%%%%%%%%%%%%%%
% (MIT License)
% Below is a simple geo-fencing API script. 
% It computes whether two points is within 100 km radius of each other 
% and prints true or false to be sent as the HTTP response data. 
% SaturnParams is a cell array containing the latitude and longitude of the two points.
% For instance, SaturnParams='{13.648416, 100.482074, 13.745675, 100.582083}'
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

radius=6371; %radius of Earth in km

lat1=SaturnParams{1}*pi/180;
lon1=SaturnParams{2}*pi/180;
lat2=SaturnParams{3}*pi/180;
lon2=SaturnParams{4}*pi/180;

deltaLat=lat2-lat1;
deltaLon=lon2-lon1;

a=sin((deltaLat)/2)^2 + cos(lat1)*cos(lat2) * sin(deltaLon/2)^2;
c=2*atan2(sqrt(a),sqrt(1-a));

% Calculate Haversine distance
distance_km=radius*c; 

if (distance_km < 20)
  printf("true");
else
  printf("false");
endif
```
