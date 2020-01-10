import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.OutputStreamWriter;
import java.net.HttpURLConnection;
import java.net.URL;
import java.net.URLConnection;
import java.net.URLEncoder;

public class Samplesmsapp 
	
{
	public static String sendSms()
	{
	try {
		// Construct data
		String apiKey = "apikey=" + " gZiUL9RvVro-M6HEmdMAfItmSm03aC0nrttxXm3XUR";
		String message = "&message=" + "Hai Dear";
		String sender = "&sender=" + "Sneha";
		String numbers = "&numbers=" + "918123456789"; //Telephone no of sender
		
		// Send data
		HttpURLConnection conn = (HttpURLConnection) new URL("https://api.textlocal.in/send/?").openConnection();
		String data = apiKey + numbers + message + sender;
		conn.setDoOutput(true);
		conn.setRequestMethod("POST");
		conn.setRequestProperty("Content-Length", Integer.toString(data.length()));
		conn.getOutputStream().write(data.getBytes("UTF-8"));
		final BufferedReader rd = new BufferedReader(new InputStreamReader(conn.getInputStream()));
		final StringBuffer stringBuffer = new StringBuffer();
		String line;
		while ((line = rd.readLine()) != null) {
			stringBuffer.append(line);
		}
		rd.close();
		
		return stringBuffer.toString();
	} catch (Exception e) {
		e.printStackTrace();

		System.out.println("Error SMS "+e);
		return "Error "+e;
	}
}
	public static void main(String[] args){
		String test = "";
		test = sendSms();
		
		
	}

}


	
