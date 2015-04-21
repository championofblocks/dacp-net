# Introduction #

Sorry there is not more detail here but the main thing you need is to implement the abstract class DACPServer.  You must implement all of it for it to work properly and you will need to investigate each call to see what it should return and how you would return it for your specific application.


# Details #

Implement the DACPServer abstract class.

```
	/// <summary>
	/// Description of MyDacpServer.
	/// </summary>
	public class MyDacpServer:DACPServer
	{
		
		// constants
		public const string APPLICATION_NAME = "MyDacpServer";
		
				// logger
		private static readonly ILog LOG = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);
		
#region Initialization
		/// <summary>
		/// Constructor to initialize Log4NET
		/// </summary>
		public MyDacpServer():base()
		{
			try {
				// initialize log4net by getting EXE path
				FileInfo exeFile = new System.IO.FileInfo(Application.ExecutablePath);
				string log4netFile = exeFile.Directory.FullName + "\\"+APPLICATION_NAME+".log4net";
				FileInfo configFile = new System.IO.FileInfo(log4netFile);
				XmlConfigurator.ConfigureAndWatch(configFile);
				LOG.InfoFormat("*** Creating Server {0} ***", this.Version);
			} catch (Exception ex) {
				LOG.Error("Server Error: " + ex.Message, ex);
			}
		}
		
		/// <summary>
		/// Application name for this DACP Server
		/// </summary>
		/// <returns>the name of this DACP Server</returns>
		public override string GetApplicationName() {
			return APPLICATION_NAME;
		}
		
		/// <summary>
		/// Starts the server.
		/// </summary>
		protected override void Start() {
			LOG.InfoFormat("Initializing {0}...", this.GetApplicationName());
			try {
				base.Start();
			} catch (DACPBonjourException) {
				MessageBox.Show("Bonjour is required by this application and it was not found.  A browser will be opened to a download page.  Please install Bonjour For Windows", "Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
				System.Diagnostics.Process.Start("http://support.apple.com/downloads/Bonjour_for_Windows");
			} catch (Exception ex) {
				LOG.Error(this.GetApplicationName() + " Server Error: " + ex.Message, ex);
				MessageBox.Show(this.GetApplicationName() + " Error: " + ex.Message, this.GetApplicationName() + " Server Error", MessageBoxButtons.OK, MessageBoxIcon.Error);
			}
		}

		/// <summary>
		/// Stops the server.
		/// </summary>
		protected override void Stop() {
			LOG.InfoFormat("Shutting Down {0}...", this.GetApplicationName());
			try {
				base.Stop();
			} catch (Exception ex) {
				LOG.Error("Stop Error: " + ex.Message, ex);
			}
		}
#endregion	

		/// <summary>
		/// Event fired when the DACP Client is discovered using mDNS .
		/// </summary>
		public override void OnClientListChanged()
		{
			throw new NotImplementedException();
		}
		
	
#region DACP Implementation Calls
		protected override void SetSpeakers(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse SetProperty(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void SetPlaylist(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		public override void RefreshCache()
		{
			throw new NotImplementedException();
		}
		
		protected override void QueueTracks(System.Net.HttpListenerRequest request, bool clearQueue, bool beginPlaying)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistRename(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistRemoveTrack(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistRemove(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistRefresh(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistMoveTrack(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistAddTrack(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse PlaylistAdd(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void Logout(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetUpdate(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetTracks(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetSpeakers(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetProperty(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetPlaylistTracks(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetPlaylists(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetNowPlaying(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetGenres(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetDatabaseInfo(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetCurrentPlayerStatus(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetComposers(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetArtworkResponse(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetArtists(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override DACPResponse GetAlbums(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlStop(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlShuffle(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlRewind(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlRepeat(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlPreviousItem(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlPlayResume(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlPlayPause(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlPause(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlNextItem(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlGeniusSeed(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlFastForward(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
		
		protected override void ControlClearQueue(System.Net.HttpListenerRequest request)
		{
			throw new NotImplementedException();
		}
#endregion
	}


```


For a specific method you will have to fill out its DACP Response based on your server.   For example below is the return for the GetDatabaseInfo call the DACP client will make to find out information about your library.

```
		/// <summary>
		/// For a Database request return the Database information.
		/// </summary>
		/// <param name="request">the HTTP Request</param>
		/// <returns>a DatabaseResponse with all the information</returns>
		protected override DACPResponse GetDatabaseInfo(HttpListenerRequest request) {
			DatabaseResponse dbResponse = new DatabaseResponse(request);
			dbResponse.Minm = this.GetApplicationName();
			dbResponse.Miid = MediaMonkey.Database.DatabaseID;
			dbResponse.Mper = (ulong)MediaMonkey.Database.DatabaseID;
			int playlistCount = RecordCount("PLAYLISTS", "PLAYLISTS.IDPlaylist", "WHERE Playlists.IsAutoPlaylist IS NULL");
			if (playlistCount == 0) {
				// default to 1 because the iPad requires at least one playlist
				playlistCount = 1;
			}
			dbResponse.Mctc = playlistCount;
			return dbResponse;
		}
```