public class MainActivity extends AppCompatActivity implements LocationListener {
    LocationManager locationManager;
    LocationListener locationListener;
    TextView t1;
    @RequiresApi(api = Build.VERSION_CODES.M)
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        t1 = findViewById(R.id.add);
        locationManager = (LocationManager) getSystemService(Context.LOCATION_SERVICE);
        if (ActivityCompat.checkSelfPermission(this, android.Manifest.permission.ACCESS_FINE_LOCATION)!= PackageManager.PERMISSION_GRANTED && ActivityCompat.checkSelfPermission(this,android.Manifest.permission.ACCESS_COARSE_LOCATION)!= PackageManager.PERMISSION_GRANTED)
        {
            ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.ACCESS_FINE_LOCATION}, 100);
        }
        locationManager.requestLocationUpdates(LocationManager.GPS_PROVIDER,0,0, this);
    }
    @Override
    public void onLocationChanged(Location location)
    {
        t1 = findViewById(R.id.add);
        t1.setText("Latitude : "+location.getLatitude()+", Longitude : "+location.getLongitude());
    }
    @Override
    public void onStatusChanged(String s,  int i, Bundle bundle)
    {
        Log.d("Latitude","status");
    }
    @Override
    public void onProviderEnabled(String s)
    {
        Log.d("Latitude","enable");
    }
    @Override
    public void onProviderDisabled(String s)
    {
        Log.d("Latitude","disable");
    }
}


GPS Location - Record updated code
