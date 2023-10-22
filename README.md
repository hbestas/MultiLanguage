# MultiLanguage
Multi Language 

----------------------------------------------------------------------------------------------------------------------

Database Table Create
 ...
CREATE TABLE [dbo].[LocalizerResource](
	[Id] [uniqueidentifier] NOT NULL,
	[LanguageCode] [nvarchar](256) NULL,
	[Key] [nvarchar](256) NULL,
	[Value] [nvarchar](MAX) NULL,
	[Description] [nvarchar](1024) NULL,
	[Tag] [nvarchar](128) NULL,
	[IsActive] [bit] NOT NULL,
	[IsDeleted] [bit] NOT NULL,
	[CreatedAt] [datetimeoffset](7) NOT NULL
 CONSTRAINT [PK_LocalizerResource] PRIMARY KEY CLUSTERED 
(
	[Id] ASC
)WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
 ...

----------------------------------------------------------------------------------------------------------------------

Startup.cs Example...

    public void ConfigureServices(IServiceCollection services)
    { 
        ...
        services.AddLocalizer(connectionString);
        ...
    }
   
   
----------------------------------------------------------------------------------------------------------------------


Controller Example...


    public class WeatherForecastController : ControllerBase
    {
        private readonly ILocalizerResourceManager _resourceManager;
        private readonly DataContext _context;

        public WeatherForecastController(ILocalizerResourceManager resourceManager, DataContext context)
        {
            _resourceManager = resourceManager;
            _context = context;
        }

        [HttpGet]
        public string Get()
        {
            var data = _context.Set<Address>().Where(x => x.IsActive).ToList();

            var resourceValue = _resourceManager.GetResource("portal_global_ok");

            return "";
        }
    }


----------------------------------------------------------------------------------------------------------------------

Suggestion...

- It is recommended to use the key names as the example below for cache etc. case.  ("portal_global_ok", "api_member_getmember_error")
( "portal name" _ "controller name" _ "method name" _ "button name" )
- All keys with the word global in their name can be used jointly.

----------------------------------------------------------------------------------------------------------------------


You can get paid support for faster use and integration with Cache.
hbestas@teknolojik.net

  
