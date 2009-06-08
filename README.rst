==================
python-crpapi
==================

Python library for interacting with the CRP API.

Based on python-sunlightapi, a project of Sunlight Labs (c) 2008.  
Written by James Turk <jturk@sunlightfoundation.com>.

All code is under a BSD-style license, see LICENSE for details.


Requirements
============

python >= 2.4

simplejson >= 1.8 (not required with python 2.6, will use built in json module)


Installation
============
To install run

    python setup.py install

which will install the bindings into python's site-packages directory.

Usage
=====

To initialize the api, all that is required is for it to be imported and for an
API key to be defined.

(If you do not have an API key visit http://www.opensecrets.org/api/admin/ to
register for one.)

Import modules:
    
    >>> from crpapi import CRP, CRPApiError
    
And set your API key:
    
    >>> CRP.apikey = 'yr-api-key'

See below for specific method usage
	
=======
Methods
=======
Candidate Methods:
	candSummary:
		>>> print CRP.candSummary.get(cid='N00007360',cycle='2010')
		{u'origin': u'Center for Responsive Politics', u'next_election': u'2010', u'debt': u'0', u'last_updated': u'03/31/2009', u'cand_name': u'Pelosi, Nancy', u'cid': u'N00007360', u'spent': u'471725', u'chamber': u'H', u'state': u'CA', u'first_elected': u'1987', u'source': u'http://www.opensecrets.org/politicians/summary.php?cid=N00007360&cycle=2010', u'party': u'D', u'total': u'377304', u'cash_on_hand': u'221291', u'cycle': u'2010'}
		
	candContrib:
		>>> for cont in CRP.candContrib.get(cid='N00007360',cycle='2010'):
		...		print cont
		Akin, Gump et al 18400
		American Dental Assn 10000
		Hercules Holding 10000
		Intl Brotherhood of Electrical Workers 10000
		Machinists/Aerospace Workers Union 10000
		New York Life Insurance 10000
		Operating Engineers Union 10000
		Air Line Pilots Assn 5000
		American Academy of Dermatology Assn 5000
		American Fedn of St/Cnty/Munic Employees 5000
		Amgen Inc 5000
		Dean Foods 5000
		Marine Engineers Beneficial Assn 5000
		Metlife Inc 5000
		National Beer Wholesalers Assn 5000
		National Venture Capital Assn 5000
		Natl Cmte to Preserve Social Security 5000
		Sony Corp 5000
		Transport Workers Union 5000
		United Transportation Union 5000

	candIndustry:
		>>> for ind in CRP.candIndustry.get(cid='N00007360',cycle='2010'):
		...     print ind
		Lawyers/Law Firms 23400
		Industrial Unions 22500
		Transportation Unions 22500
		Health Professionals 20000
		Insurance 15000
		Building Trade Unions 13500
		Lobbyists 10800
		Hospitals/Nursing Homes 10000
		TV/Movies/Music 8000
		Securities & Investment 7500
		Public Sector Unions 7000
		Misc Issues 5000
		Telecom Services & Equipment 5000
		Dairy 5000
		Pharmaceuticals/Health Products 5000
		Beer, Wine & Liquor 5000
		Real Estate 3500
		Accountants 2500
		Electric Utilities 2500
		Construction Services 2500
		Retail Sales 2500
		Railroads 2500
		Food & Beverage 2500
		Misc Business 2500
		Business Services 1000
		Misc Defense 1000
		Automotive 500
		Environment 500

	candIndByInd:
		>>> print CRP.candIndByInd.get(cid='N00007360',cycle='2010',ind='H01')
		{u'origin': u'Center for Responsive Politics', u'last_updated': u'4/27/09', u'cand_name': u'Pelosi, Nancy', u'cid': u'N00007360', u'industry': u'Health Professionals', u'pacs': u'20000', u'rank': u'0', u'indivs': u'0', u'chamber': u'', u'state': u'California', u'source': u'http://www.opensecrets.org/industries/recips.php?Ind=H01&cycle=2010&recipdetail=&Mem=Y&sortorder=U', u'party': u'D', u'total': u'20000', u'cycle': u'2010'}

		candSector:
		>>> for sec in CRP.candSector.get(cid='N00007360',cycle='2010'):
		...     print sec
		Agribusiness 5000
		Communic/Electronics 13000
		Construction 2500
		Defense 1000
		Energy/Nat Resource 2500
		Finance/Insur/RealEst 28500
		Health 35000
		Lawyers & Lobbyists 34200
		Transportation 3000
		Misc Business 13500
		Labor 65500
		Ideology/Single-Issue 5500

Member Methods:
	memTravelTrips:
		>>> for trip in CRP.memTravelTrips.get(cid='N00000019',year='2006'):
		...     print trip
		Tamera S. Luzzatto Israel
		Melissa Ho New York City, New York
		Amitabh Desai New York, New York
		Tamera S. Luzzatto Boston, Massachusetts
		Tamera S. Luzzatto Binghamton, New York
		Andrew Shapiro Binghamton, New York
		Hillary Rodham Clinton Dulles, Virginia
		Huma Abedin Dulles, Virginia
		Gregory M. Walton Long Beach, California
		Tamera S. Luzzatto Denver, Colorado
		Laurie Rubiner Denver, Colorado
		Huma Abedin Denver, Colorado
		Hillary Rodham Clinton Denver, Colorado
		Lorraine Voles Buffalo, New York
		Laurie Rubiner Germany
		Andrew Shapiro Montebello, New York
		Huma Abedin New York, New York
		Hillary Rodham Clinton New York, New York
		Ann Gavaghan Durham, North Carolina
		Kris M. Balderston New York, New York
		Joshua Williams New York, New York
		Huma Abedin Charleston, South Carolina
		Hillary Rodham Clinton Charleston, South Carolina